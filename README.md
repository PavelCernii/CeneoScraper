# CeneoScraper 

## Kod produktu do tesów
84514582

## Algorytm pobirania opinii o produkcie z serwisu Ceneo.pl
1. Wysłanie żądania dostępu do strony internretowej z opiniami o produkcie 
2. Jeżeli operacja zakończy się powozeniem, weodrębnienie w kodu strony opini o produkcie 
3. Dla każdej opinii wyodrębnienie z kodu HTML poszczególnych składowych i przysylanie ich do elementów zlożonej struktury danych
4. JEśli istneje kolejna strona z opiniami, przejście do niej i powtórzen dla niej kroków 1-4
5. Zapisanie wyników do bazy danych 

## Struktura opinii w serwisie Ceneo.pl 
|składowa|zmienna|selektor|
|--------|-------|--------|
|opinia|review|div.js_product-review:not(.user-post--highlight)|
|identyfikator opinii|opinion_id|['data-entry-id']|
|autor|author|span.user-post__author-name|
|rekomendacja|recommendation|span.user-post__author-recomendation > em|
|liczba gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|lista zalet|pros|div.review-feature__item--positive|
|lista wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|useful|button.vote-yes > span|
|ile osób uznało opinię za nieprzydatną|unuseful|button.vote-no > span|
|data wystawienia opinii|post_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|purchase_date|time:nth-child(2)['datetime']|
