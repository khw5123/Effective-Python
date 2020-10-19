# PEP 8 스타일 가이드 일부

* 들여쓰기는 탭이 아닌 스페이스로 한다.

* 들여쓰기는 스페이스 네 개를 사용한다.

* 한 줄의 문자 길이는 79자 이하여야 한다.

* 표현식이 길어져서 다음 줄로 이어질 경우 추가로 스페이스 네 개를 사용한다.

* 파일에서 함수와 클래스는 빈 줄 두개로 구분한다.

* 클래스에서 메서드는 빈 줄 하나로 구분한다.

* 리스트 인덱스, 함수 호출, 키워드 인수 할당에는 스페이스를 사용하지 않는다.

* 변수 할당 앞뒤에 스페이스를 하나만 사용한다.
<pre><code>
value = 5
</code></pre>

* 함수, 변수, 속성은 lowercase_underscore 형식을 따른다.

* protected 인스턴스 속성은 _leading_underscore 형식을 따른다.(앞에 언더바 한 개)

* private 인스턴스 속성은 __double_leading_underscore 형식을 따른다.(앞에 언더바 두 개)
<pre><code>
class Movie:
    def __init__(self, movie_name):
        self.__movie_name = movie_name # private 멤버 변수
 
    @property # property 데코레이터
    def movie_name(self): # 메서드 이름은 멤버 변수의 이름과 동일하게
        return self.__movie_name
 
    @movie_name.setter # setter 데코레이터
    def movie_name(self, new_movie_name): # 메서드 이름은 멤버 변수의 이름과 동일하게
        self.__movie_name = new_movie_name

movie = Movie('라라랜드')
print(movie.movie_name)
movie.movie_name = '인셉션' # 멤버 변수에 직접 접근하는 것처럼 보이지만 실제로는 setter 메서드를 통해 변수에 접근
print(movie.movie_name)
</code></pre>

* 클래스와 예외는 CapitalizedWord 형식을 따른다.

* 모듈 수준 상수는 ALL_CAPS 형식을 따른다.

* 클래스의 인스턴스 메서드에서는 첫 번째 파라미터의 이름을 self로 지정한다.

* 클래스 메서드에서는 첫 번째 파라미터의 이름을 cls로 지정한다.
<pre><code>
class Test:
    classVariable = 0
    
    def __init__(self):
        self.__privateVariable = 0
    
    def getPrivateVariable(self):
        return self.__privateVariable
    
    def setPrivateVariable(self, n):
        self.__privateVariable = n
    
    @classmethod # 클래스 메서드
    def getClassVariable(cls): # 첫 번째 파라미터의 이름은 cls
        cls.classVariable += 1
        return cls.classVariable

print(Test.getClassVariable())
print(Test.getClassVariable())
test = Test()
test.setPrivateVariable(10)
print(test.getPrivateVariable())
test._Test__privateVariable = 20 # _클래스 + private 멤버 변수 형태로 접근 가능
print(test.getPrivateVariable())
</code></pre>

* 긍정 표현식의 부정(if not a is b) 대신에 인라인 부정(if a is not b)을 사용한다.

* 길이를 확인(if len(someList) == 0)하여 빈 값([] or '')을 확인하지 않는다. if not someList를 사용하고, 빈 값은 암시적으로 False가 된다고 가정한다.

* 한 줄로 된 if문, for와 while루프, except 복합문을 쓰지 말고 여러 줄로 나눠서 작성한다.

* 항상 파일의 맨 위에 import 문을 놓는다.

* 모듈을 임포트할 때는 항상 모듈의 절대 이름을 사용하며 현재 모듈의 경로를 기준으로 상대 경로로 된 이름을 사용하지 않는다.
ex) bar 패키지의 foo 모듈을 임포트할 때 import foo가 아닌 from bar import foo라고 해야 한다.

* 상대적인 임포트를 해야 한다면 명시적으로 작성한다.
<pre><code>
from . import foo
</code></pre>

* 임포트는 표준 라이브러리 모듈, 서드파티 모듈, 사용자 정의 모듈 섹션 순으로 구분한다. 각각의 하위 섹션에서는 알파벳 순서로 임포트한다.

+ 전체 PEP 8 스타일 가이드: https://www.python.org/dev/peps/pep-0008