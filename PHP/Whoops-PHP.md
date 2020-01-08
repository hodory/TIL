# array_merge() 의 파라미터로 배열이 아닌 값을 받으면 Null을 리턴합니다.
```php
public function testArrayMergeReturnsNull()
{
    $str = 'Have A Nice Day';
    $aTest = [
        $str
    ];
 
    $this->assertNull(array_merge($aTest, null));
    $this->assertNull(array_merge($aTest, 10));
    $this->assertNull(array_merge($aTest, 'String'));
}
```