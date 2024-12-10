Pytanie 3.1
Testy mogłyby przestać działać poprawnie, ponieważ:
-@BeforeEach uruchamia metodę przed każdym testem, co oznacza, że każda metoda testowa otrzymuje nową instancję obiektu testowego (np. Calculator), co zapewnia niezależność testów.
-@BeforeAll uruchamia metodę tylko raz przed wszystkimi testami, co może powodować problemy, jeśli testy modyfikują stan obiektu, ponieważ wszystkie testy korzystają z tej samej instancji.

Pytanie 4.1
Failure: Oznacza, że warunek asercji nie został spełniony. W przypadku testów będzie to metoda, w której wyrażenie asercji zwróci fałsz. W tym przypadku jest to metoda test1.
Error: Oznacza, że test zakończył się nieprzewidzianym wyjątkiem. Metoda z rzucanym wyjątkiem zostanie oznaczona jako Error. W tym przypadku jest to metoda test2.

Pytanie 4.2
JUnit oczekuje rzucenia wyjątku klasy org.opentest4j.AssertionFailedError dla oznaczenia Failure. Jest to wyjątek generowany w przypadku niespełnienia warunku asercji w JUnit.

Pytanie 5.1
To typ testowania whitebox, ponieważ analiza ścieżek wymaga znajomości wewnętrznej struktury metody i kodu źródłowego.

Pytanie 5.2
Liczba możliwych ścieżek: 4.
Każda ścieżka odpowiada jednemu z możliwych wyników metody w zależności od stanu obiektu Customer.