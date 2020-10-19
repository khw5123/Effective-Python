# bytes, str, unicode 차이

* python3 에서는 bytes와 str 두 가지 타입으로 문자를 나타낸다. bytes 인스턴스는 raw 8비트 값을 저장한다. str 인스턴스는 유니코드 문자를 저장한다.

* python2 에서는 str과 unicode 두 가지 타입으로 문자를 나타낸다. str 인스턴스는 raw 8비트 값을 저장한다. unicode 인스턴스는 유니코드 문자를 저장한다.

python3 에서 유니코드 문자를 바이너리 데이터로 변환하려면 encode 메서드 사용
<pre><code>
def to_bytes(bytes_or_str):
    if isinstance(bytes_or_str, str):
        value = bytes_or_str.encode('utf-8')
    else:
        value = bytes_or_str
    return value  # Instance of bytes

print(repr(to_bytes(b'foo')))
print(repr(to_bytes('foo')))
</code></pre>

python3 에서 바이너리 데이터를 유니코드 문자로 변환하려면 decode 메서드 사용
<pre><code>
def to_str(bytes_or_str):
    if isinstance(bytes_or_str, bytes):
        value = bytes_or_str.decode('utf-8')
    else:
        value = bytes_or_str
    return value  # Instance of str

print(repr(to_str(b'foo')))
print(repr(to_str('foo')))
</code></pre>

* python3 에서 내장 함수 open이 반환하는 파일 핸들을 사용하는 연산은 기본으로 UTF-8 인코딩을 사용한다. python2 에서 파일 연산은 기본으로 바이너리 인코딩을 사용한다.

* python2와 python3 에서의 올바른 open 사용법
<pre><code>
with open('/test', 'wb') as f: # 'w'로 바이너리 데이터를 파일에 기록하려 한다면 python3 에서 동작하지 않음
    f.write()
</code></pre>