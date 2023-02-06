---
title: CodeIgniter4 구성파일
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Codeigniter4 Configuration

#### 구성파일 (Configuration)
- 매개 변수 / 초기 설정 등의 공용 속성인 단순 클래스 정의
- /app/Config 폴더
- 구성 파일 Access 방법
    ```
    // 구성 객체 생성
    $config = new \Config\Pager();  
    
    // config() function 사용
    // config() 함수로 공유 인스턴스 가져 오기
    $config = config( 'Pager' );
    
    // 네임스페이스가 있는 config 클래스에 액세스합니다.
    $config = config( 'Config\\Pager' );
    
    // config() 함수를 사용하여 새 객체 생성
    $config = config('Pager', false);
    // 클래스 속성으로 설정에 액세스합니다.
    $pageSize = $config->perPage;
    ```
- namespace 없다면 /app/Config/와 정의된 모든 네임스페이스에서 파일 찾음

#### 구성 파일 만들기
- CodeIgniterConfigBaseConfig 확장해 생성(환경별로 설정을 상속받을 수 있도록 고려)
    ```
    <?php        
    namespace Config;        
    use CodeIgniter\Config\BaseConfig;
    
    class CustomClass extends BaseConfig
    {
        public $siteName  = 'My Great Site';
        public $siteEmail = 'webmaster@example.com';        
    }
    ```

#### 환경 변수
- Local / 개발 / Production 등 여러 환경에 따라 다른 구성 값이 필요한 경우 사용
- ex. API키 / 개인 데이터 등
- root 폴더에 env 파일
- 소스 관리에 env 파일 업로드에 대해서는 고민 필요 ( 중요 정보 업로드 될 수 있기 때문 )
- 어플리케이션이 실행되면 .env 가 자동으로 로드되고 변수가 환경 ( 단, 환경에 변수가 이미 있는 경우 이 변수를 덮어쓰지 않음 )
- var_dump($_ENV) 또는 phpinfo()를 통해 중요한 보안 관련 데이터가 공개적으로 노출될 수 있음
    ```
    // key = value 로 설정
    S3_BUCKET = dotenv
    SECRET_KEY = super_secret_key
    CI_ENVIRONMENT = development

    //getenv()함수 / $_SERVER or $_ENV 사용
    $s3_bucket = getenv('S3_BUCKET');
    $s3_bucket = $_ENV['S3_BUCKET'];
    $s3_bucket = $_SERVER['S3_BUCKET'];
    ```

#### 중첩 변수
- 공통된 변수 재사용
- $(...) 묶어 사용
    ```
    BASE_DIR="/var/webroot/project-root"
    CACHE_DIR="${BASE_DIR}/cache"
    TMP_DIR="${BASE_DIR}/tmp"
    ```

#### 네임스페이스 변수
- 이름이 같은 변수
    ```
    // 네임스페이스 변수 아님
    name = "George"
    db=my_db
    
    // 네임스페이스 변수
    address.city = "Berlin"
    address.country = "Germany"
    frontend.db = sales
    backend.db = admin
    BackEnd.db = admin
    ```

#### 구성 클래스 및 환경 변수
- 구성 클래스를 객체화 하면 구성 개체의 속성에 병합하기 위한 namespaced 환경변수가 고려됨
- 네임스페이스가 지정된 변수의 접두사가 구성 클래스의 네임스페이스와 정확히 일치하면 설정의 흥행 부분이 구성속성으로 처리됨
- 기존 구성 속성과 일치하면 환경 변수의 값이 구성 파일의 해당 값을 대체
- 일치하는 항목이 없으면 구성 클래스 속성 변경되지 않음
- 대소문자 구분 네임스페이스 사용
- env에 포함된 환경변수는 구성파일의 기존 데이터를 대체할 뿐
- env는 구성파일의 값을 채우거나 교체하는 역할만 ( 구성파일에 container or 수신 속성 존재 필요 )

#### 환경변수를 배열로 처리
- namespace 환경변수는 배열로 처리 가능
- 접두사가 구성클래스와 일치하면 나머지 환경변수 이름도 .을 포함하는 경우 배열로 처리됨
    ```
    // 정규 네임스페싱 변수
   Config\SimpleConfig.name = George
   
   // 배열 네임스페싱 변수
   Config\SimpleConfig.address.city = "Berlin"
   Config\SimpleConfig.address.country = "Germany"
    ```

#### 레지스터(Registers)
- 추가 구성 속성을 제공하는 다른 클래스
- 네임스페이스와 파일에 걸쳐 런타임에 구성을 변경하는 방법
- env는 항상 Registers에 등록된 값보다 우선
- Config/Registrar.php

1) 암시적 레지스터
- 제3자 모듈은 개발이 이미 구성한 내용을 덮어쓰지 않고 Pager에 추가 템플릿을 제공
    ```
    class Registrar
    {
            public static function Pager(): array
            {
                    return [
                            'templates' => [
                                    'module_pager' => 'MyModule\Views\Pager',
                            ],
                    ];
            }
    }
    ```
2) 명시적 레지스터
- 구성 파일은 레지스터 수를 명시적으로 지정 가능
- registers 의 변수가 동일한 경우 데이터는 registers 우선
    ```
    <?php namespace App\Config;
    use CodeIgniter\Config\BaseConfig;
    
    class MySalesConfig extends BaseConfig
    {
        public $target            = 100;
        public $campaign          = "Winter Wonderland";
        public static $registrars = [
            '\App\Models\RegionalSales';
        ];
    }
    ```

<br>
<br>
###### #Reference
{: .text-right }
[구성파일작업](http://ci4doc.cikorea.net/general/configuration.html)
{: .text-right }


