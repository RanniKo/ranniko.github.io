---
title: CodeIgniter4 Example Alex's Login & Registration Tutorial 01
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

[2021-09-24-CodeIgniter4_Example00.md] 를 공부한 후 UnitTest를 붙여보도록 한다.

### CodeIgniter UnitTest
권장방법 : Composer
```
    // root directory에서 실행
    > composer require --dev phpunit/phpunit
```

단위테스트 실행
```
    > ./vendor/bin/phpunit
```

### Test Class
```
    <?php
    namespace App\Models;
    //CIUnitTestCase 확장
    use CodeIgniter\Test\CIUnitTestCase;
    
    class OneOfMyModelsTest extends CIUnitTestCase
    {
        public function testFooNotBar()
        {
            // ...
        }
    }
```

### TestCase에 대한 준비 방법
```
    // 정적 메소드는 전체 테스트 케이스 전후에 실행
    public static function setUpBeforeClass(): void
    public static function tearDownAfterClass(): void
```
```
    // 아래 메소드는 각 테스트 사이에 실행
    public function setUp(): void
    public function tearDown(): void
```

PHP는 rebuild 없이, 바로 반영되고 원격 서버의 소스까지 Debugging이 가능


<br>
<br>
###### #Reference
{: .text-right }
[CodeIgniter URL](https://github.com/alexlancer/codeigniter4login)
{: .text-right }
