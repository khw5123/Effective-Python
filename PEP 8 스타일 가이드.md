
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




- 전체 가이드: https://www.python.org/dev/peps/pep-0008