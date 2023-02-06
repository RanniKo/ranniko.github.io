---
title: CodeIgniter4 Example Alex's Login & Registration Tutorial 00
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Codeigniter4 Example
어떻게 구조를 이해할까 고민하다 발견
https://github.com/alexlancer/codeigniter4login

4 버전에 해당하는 쉬운 소스 찾기가 힘든데, Alex 님이 잘 정리해놨다.
심지어 동영상까지 있어서, 하나씩 작업하면서 구조나 많이 사용하는 함수에 대해 공부 가능!

이 소스 이용해서, 좀 확장 버전으로 만들어서 push 해야겠다.
* [CodeIgniter 4 Login & Registration Tutorial](https://www.youtube.com/watch?v=wPjK42v1oAs&list=PLYogo31AXFBONHR0WjlnhxN4ulRrF98aA&index=3)

#### 설정01
public\index.html에 추가 ( page error logging 표시 )

아래 설정이 없는 경우, whoops 페이지를 마주해 오류내용을 확인하기 어렵다.

```
define("ENVIRONMENT","development");
```

#### troubleshooting01
```
redirect()->to('dashboard');
```

redirect 가 계속 아래와 같은 index.php 가 붙어서 동작하는 현상 확인

![ci4_ex01_ts01](/assets/img/ci4_ex01_ts01.png)

원인은 나의 "Config\App.php" 파일에 $indexPage 의 Value가 index.php로 되어있었기 때문!!
```
//as-is
public $indexPage = 'index.php';
//to-be
public $indexPage = '/';
```

#### 참고 Validation Message 변경
validation message 변경을 위해 3가지 방법을 시도해봄
```
    // 1) rules와 errors 에 각각 설정 validateUser, validateEmail UserRules.php에 정의한 method
    $rules = [
        'email' => 'required|min_length[6]|max_length[50]|validateEmail[email]',
        'password' => 'required|min_length[8]|max_length[255]|validateUser[password]',
    ];

    $errors = [
        'email' => [
            'validateEmail' => '입력한 이메일 없음',
            'required' => '이메일:필수오류!',
            'min_length' => '이메일:최소 6자 이상 입력 필요',
            'max_length' => '이메일:최대 50글자임!',
        ],
        'password' => [
            'validateUser' => '비밀번호 다름',
            'required' => '비번:필수오류!',
            'min_length' => '비번:최소 8자 이상 입력 필요',
            'max_length' => '비번:최대 255글자임!',
        ]
    ];
    if(! $this->validate($rules, $errors)) {
        $data['validation'] = $this->validator;
    }
```
<br>
```
    // 2) setRules로 설정 validateUser, validateEmail UserRules.php에 정의한 method
    $setRules = ([
        'email' => [
            'label'  => 'Username',
            'rules'  => 'required|min_length[6]|max_length[50]|validateEmail[email]',
            'errors' => [
                'validateEmail' => '입력한 이메일{field}:({value}) 없음',
                'required' => '이메일:필수오류!',
                'min_length' => '이메일:최소 6자 이상 입력 필요',
                'max_length' => '이메일:최대 50글자임!',
            ],
        ],
        'password' => [
            'label'  => 'Password',
            'rules'  => 'required|min_length[8]|max_length[255]|validateUser[password]',
            'errors' => [
                'validateUser' => '비밀번호 다름',
                'required' => '비번:필수오류!',
                'min_length' => '비번:최소 8자 이상 입력 필요',
                'max_length' => '비번:최대 255글자임!',
            ],
        ]
    ]);
    
    if(! $this->validate($setRules)) {
        $data['validation'] = $this->validator;
    }
```
<br>
```
    // 3) Errors.php로 Localization file 생성 후 해당하는 message 사용
    // 정의부분 ( Language\ko\Errors.php )
    <?php    
    return [
        'errorRequiredEmailMissing'    => '이메일:필수오류!',
        'errorValidateEmail' => '입력한 이메일{field}:({value}) 없음',
        'errorPassword' => [
            'maxLength'      => '비번:최대 255글자임!',
            'minLength'      => '비번:최소 8자 이상 입력 필요',
            'validateUser'      => '비밀번호 다름',
            'required'      => '비번:필수오류!!!',
        ],
    ];
    
    // 호출 부분 ( Controller\Users.php )
    $setRules = ([
        'email' => [
            'label'  => 'email',
            'rules'  => 'required|min_length[6]|max_length[50]|validateEmail[email]',
            'errors' => [
                'validateEmail' => '입력한 이메일{field}:({value}) 없음',
                'required' => lang('Errors.errorRequiredEmailMissing'),
                'min_length' => '이메일:최소 6자 이상 입력 필요',
                'max_length' => '이메일:최대 50글자임!',
            ],
        ],
        'password' => [
            'label'  => 'Password',
            'rules'  => 'required|min_length[8]|max_length[255]|validateUser[password]',
            'errors' => [
                'validateUser' => lang('Errors.errorPassword.validateUser'),
                'required' => lang('Errors.errorPassword.required'),
                'min_length' => lang('Errors.errorPassword.minLength'),
                'max_length' => lang('Errors.errorPassword.maxLength'),
            ],
        ]
    ]);

    if(! $this->validate($setRules)) {
        $data['validation'] = $this->validator;
    }
```
<br>
#### 참고 Users.php에 반복되는 helper load
```
    // Users.php가 상속받는 BaseController에 미리 설정
    // 프로젝트가 실행될 때마다 사용할 헬퍼, 모델, 라이브러리, 서비스등을 로드하기에 좋은 장소
    class BaseController extends Controller
    {
        ...
        protected $helpers = ['form'];
        ...
    }
    //로드할 다른 구성 요소나 처리할 데이터는 생성자 BaseController.initController()에 추가
```

#### 참고 getSegment
- 슬래시 사이의 경로의 각 섹션은 단일 세그먼트
- URI 클래스는 세그먼트 값이 무엇인지 판별하는 간단한 방법을 제공
- 세그먼트는 경로에서 가장 왼쪽부터 인덱스는 1로 시작
```
    // URI = http://example.com/users/15/profile
    
    // Prints '15'
    if ($uri->getSegment(1) == 'users') {
            echo $uri->getSegment(2);
    }
```
<br>
#### 참고 Model 정의 시 PK를 정의 안하면 id 로 기본 값이 설정됨
PK를 정의하지 않으면, id 값으로 자동 인식된다.

이유 : Model에 protected 로 변수 존재
```
    //Model.php
    protected $primaryKey = 'id';
```
<br>
```
    // $primaryKey 재정의
    class UserModel extends Model
    {
        protected $table      = 'users';
        protected $primaryKey = 'id';
    
        protected $useAutoIncrement = true;
        ...
    }
```

<br>
#### 참고 

Alex는 bootstrap 의 css 를 사용했다.

[Boot Strap](https://getbootstrap.com/docs/5.1/getting-started/introduction/)

[password_hash 관련자료](https://www.php.net/manual/en/function.password-hash.php)

<br>
<br>
###### #Reference
{: .text-right }
[CodeIgniter URL](https://github.com/alexlancer/codeigniter4login)
{: .text-right }


