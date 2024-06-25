# Dokumentacja dataLayer dla eventów na serwisie www.inpzu.pl

Prośba o wstawienie poniższych DataLayer na strony w obrębie serwisu www.inpzu.pl.
___

## EVENTY W STRUKTURZE ECOMMERCE
### 1) Wyświetlenie listingu produktów - wywołanie eventu view_item_list

Prośba o wywołanie kodu na wyświetlenie strony z listingiem produktów na stronach z listą funduszy oraz kartą portfela.
W tablicy 'items' ma znajdować się tyle obiektów ile jest zaprezentowanych produktów na stronie. Tablica 'items' powinna się doładowywać o kolejne 'items' w momencie gdy są one widoczne dla użytkownika, czyli wraz z przewijaniem strony.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/221369c7-e1fa-4784-ba19-057ef5a58388)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item_list",
  ecommerce: {
    item_list_id: "123", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing. Wartość pobierana z góry strony, np. IKE
    items: [
     {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu dostępnego na listingu, np. inPZU Puls Życia 2025 - pole obowiązkowe
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      price: 00.00,
      quantity: 1 // liczba produktów
    },
    {
      item_id: "SKU_12346", // id drugiego produktu w tablicy, jeżeli jest dostępne 
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę drugiego produktu dostępnego na listingu, np.inPZU Puls Życia 2030 - pole obowiązkowe
      index: 1, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii drugiego produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 drugiego produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 drugiego produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 drugiego produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 drugiego produktu, jeżeli jest dostępna
      price: 00.00,
      quantity: 1 // liczba produktów
    }]
  }
});
```

### 2) Wybranie produktu - wywołanie eventu select_item
Prośba o wywołanie kodu w momencie kliknięcia w przycisk "KUP" lub "KUP ONLINE"* na stronach z listą funduszy, kartą portfela, kartą funduszu.
*W przypadku przycisku "KUP ONLINE" kod powinien być wywołany zarówno w momencie kliknięcia w górny, jak i dolny przycisk.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/eb92f011-40ea-42de-be33-3b37632d3e09)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "select_item",
  ecommerce: {
    item_list_id: "123", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing. Wartość pobierana z góry strony, np. IKE
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego został kliknięty przycisk "KUP" lub "KUP ONLINE" np. inPZU Puls Życia 2025 - pole obowiązkowe
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      price: 00.00,
      quantity: 1 // liczba produktów
    }
    ]
  }
});
```

### 3) Wyświetlenie produktu - wywołanie eventu view_item
Prośba o wywołanie kodu na wyświetlenie strony produktu na pierwszym kroku ścieżki "Podaj kwotę".
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/60835f0e-645c-48e0-994b-d3f4d5a111ce)

``` javascript 
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item",
  ecommerce: {
    currency: "PLN", // pole obowiązkowe
    value: 00.00, // pole obowiązkowe
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 00.00,
      quantity: 1
    }
    ]
  }
});
```

### 4) Dodanie produktu do koszyka - wywołanie eventu add_to_cart
Prośba o wywołanie kodu w momencie kliknięcia w przycisk "DALEJ" po prawidłowym wprowadzeniu kwoty na pierwszym kroku ścieżki "Podaj kwotę".
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/904d6ace-0e13-4f3f-b3ce-b12bea7caeb1)

``` javascript 
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_to_cart",
  ecommerce: {
    currency: "PLN", // pole obowiązkowe
    value: 100.00, // zmienna przekazująca kwotę inwestycji liczona jako price * quantity. Pole obowiązkowe
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 100.00, // zmienna przekazująca kwotę inwestycji w dany produkt. Jeżeli został wybrany więcej niż jeden produkt kwotę należy wyliczyć dla jednego określonego produktu, tj. kwota wpisana przez użytkownika * procent inwestycji danego produktu.
      quantity: 1
    }
    ]
  }
});
```


### 5) Wyświetlenie koszyka z produktem - wywołanie eventu view_cart
Prośba o wywołanie kodu na wyświetlenie strony z koszykiem produktu na drugim kroku ścieżki "Uzupełnij dane".
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/8c163966-f8ff-4999-aa64-dbdf13f86bd9)

``` javascript 
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_cart",
  ecommerce: {
    currency: "PLN", // pole obowiązkowe
    value: 100.00, // zmienna przekazująca kwotę inwestycji liczona jako price * quantity. Pole obowiązkowe
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      coupon: "[NAZWA UŻYTEGO KODU SPECJALNEGO]", // zmienna przekazująca nazwę kodu specjalnego uzupełnionego przez użytkownika
      discount: 00.00, // kwota udzielonego rabatu związanego z zastosowaniem kodu specjalnego
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 100.00, // zmienna przekazująca kwotę inwestycji w dany produkt. Jeżeli został wybrany więcej niż jeden produkt kwotę należy wyliczyć dla jednego określonego produktu, tj. kwota wpisana przez użytkownika * procent inwestycji danego produktu. Jeżeli został użyty kod rabatowy wartość price należy obniżyć o wartość z pola discount.
      quantity: 1
    }
    ]
  }
});
```


### 6) Rozpoczęcie procesu checkout - wywołanie eventu begin_checout
Prośba o wywołanie kodu na wyświetlenie strony z rozpoczęciem procesu checkout na trzecim kroku ścieżki "Wypełnij oświadczenia i ankietę".
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/e175fde7-1574-442d-b304-445c840fa306)

``` javascript 
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "begin_checkout",
  ecommerce: {
    currency: "PLN", // pole obowiązkowe
    value: 100.00, // zmienna przekazująca kwotę inwestycji liczona jako price * quantity. Pole obowiązkowe
    coupon: "[NAZWA UŻYTEGO KODU SPECJALNEGO]", // zmienna przekazująca nazwę kodu specjalnego uzupełnionego przez użytkownika
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne - pole nieobowiązkowe
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      discount: 00.00, // kwota udzielonego rabatu związanego z zastosowaniem kodu specjalnego
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 100.00, // zmienna przekazująca kwotę inwestycji w dany produkt. Jeżeli został wybrany więcej niż jeden produkt kwotę należy wyliczyć dla jednego określonego produktu, tj. kwota wpisana przez użytkownika * procent inwestycji danego produktu. Jeżeli został użyty kod rabatowy wartość price należy obniżyć o wartość z pola discount.
      quantity: 1
    }
    ]
  }
});
```

### 7) Przejście procesu checkout - wywołanie eventu add_shipping_info
Prośba o wywołanie kodu na wyświetlenie strony z kolejnym krokiem procesu checkout na czwartym kroku ścieżki "Sprawdź podsumowanie".
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/8d274a12-ca4b-4f28-a096-45bad23de9e0)

``` javascript 
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_shipping_info",
  ecommerce: {
    currency: "PLN", // pole obowiązkowe
    value: 100.00, // zmienna przekazująca kwotę inwestycji liczona jako price * quantity. Pole obowiązkowe
    coupon: "[NAZWA UŻYTEGO KODU SPECJALNEGO]", // zmienna przekazująca nazwę kodu specjalnego uzupełnionego przez użytkownika
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      discount: 00.00, // kwota udzielonego rabatu związanego z zastosowaniem kodu specjalnego
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 100.00, // zmienna przekazująca kwotę inwestycji w dany produkt. Jeżeli został wybrany więcej niż jeden produkt kwotę należy wyliczyć dla jednego określonego produktu, tj. kwota wpisana przez użytkownika * procent inwestycji danego produktu. Jeżeli został użyty kod rabatowy wartość price należy obniżyć o wartość z pola discount.
      quantity: 1
    }
    ]
  }
});
```

### 8) Poprawna weryfikacja operacji - wywołanie eventu purchase
Prośba o wywołanie kodu w momencie kliknięcia w przycisk "GOTOWE" po prawidłowym wprowadzeniu kodu z sms.
W przypadku, gdy został wybrany więcej niż jeden produkt prośba o dodanie go do tablicy items, jak w przypadku np. view_item_list.

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/40637ada-066b-4276-a96f-76e46e57c017)

``` javascript  
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "purchase",
  ecommerce: {
    transaction_id: "T_12345", // zmienna przekazująca numer zamówienia - pole obowiązkowe
    value: 100.00, // zmienna przekazująca kwotę inwestycji liczona jako price * quantity. Pole obowiązkowe
    currency: "PLN", // pole obowiązkowe
    coupon: "[NAZWA UŻYTEGO KODU SPECJALNEGO]", // zmienna przekazująca nazwę kodu specjalnego uzupełnionego przez użytkownika
    items: [
    {
      item_id: "SKU_12345", // id produktu, jeżeli jest dostępne - pole nieobowiązkowe
      item_name: "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, dla którego została wyświetlona karta produktu np. inPZU Puls Życia 2025 - pole obowiązkowe
      discount: 00.00, // kwota udzielonego rabatu związanego z zastosowaniem kodu specjalnego
      index: 0, // numer produktu na listingu
      item_brand: "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu wybranego produktu, np. IKE
      item_category: "[NAZWA KATEGORII]", // zmienna przekazująca nazwę kategorii produktu, np. Fundusz cyklu życia
      item_category2: "[NAZWA KATEGORII 2]", // zmienna przekazująca nazwę kategorii 2 produktu, jeżeli jest dostępna
      item_category3: "[NAZWA KATEGORII 3]", // zmienna przekazująca nazwę kategorii 3 produktu, jeżeli jest dostępna
      item_category4: "[NAZWA KATEGORII 4]", // zmienna przekazująca nazwę kategorii 4 produktu, jeżeli jest dostępna
      item_category5: "[NAZWA KATEGORII 5]", // zmienna przekazująca nazwę kategorii 5 produktu, jeżeli jest dostępna
      item_list_id: "123", // id listingu, jeżeli jest dostępne
      item_list_name: "[NAZWA KATEGORII FUNDUSZU/PORTFELA]", // zmienna przekazująca nazwę kategorii funduszu, którego dotyczy listing, np. IKE
      price: 100.00, // zmienna przekazująca kwotę inwestycji w dany produkt. Jeżeli został wybrany więcej niż jeden produkt kwotę należy wyliczyć dla jednego określonego produktu, tj. kwota wpisana przez użytkownika * procent inwestycji danego produktu. Jeżeli został użyty kod rabatowy wartość price należy obniżyć o wartość z pola discount.
      quantity: 1
    }
    ]
  }
});
```



___


## EVENTY W STRUKTURZE NIE ECOMMERCE

### 1) wybór odpowiedzi "TAK" na formularzu
Prośba o wywołanie kodu na kliknięcie w przycisk "TAK" w odpowiedzi na pytanie "Czy posiadasz już konto w innej instytucji finansowej?" na stronach:
* inpzu.pl/tfi/ikze-wniosek
* inpzu.pl/tfi/ike-wniosek

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/f1851de7-4d2b-429d-b05e-4d0286149301)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_TAK",
  "click_text": "[NAZWA TESKTU], //zmienna przekazująca kliknięty tekst, tu: "TAK"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, czyli "Czy posiadasz już IKE w innej instytucji finansowej?" lub "Czy posiadasz już IKZE w innej instytucji finansowej?"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, czyli np: "IKE" lub "IKZE"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "IKZE"
  "step": "0a", 
});
```

### 2) wybór odpowiedzi "NIE" na formularzu
Prośba o wywołanie kodu na kliknięcie w przycisk "NIE" w odpowiedzi na pytanie "Czy posiadasz już konto w innej instytucji finansowej?" na stronach:
* inpzu.pl/tfi/ikze-wniosek
* inpzu.pl/tfi/ike-wniosek

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/f1851de7-4d2b-429d-b05e-4d0286149301)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_NIE",
  "click_text": "[NAZWA TESKTU], //zmienna przekazująca kliknięty tekst, tu: "NIE"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, czyli "Czy posiadasz już IKE w innej instytucji finansowej?" lub "Czy posiadasz już IKZE w innej instytucji finansowej?"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, czyli np: "IKE" lub "IKZE"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "IKZE"
  "step": "0a"
});
```

### 3) wybór odpowiedzi "TAK, PRZENOSZĘ" na formularzu
Prośba o wywołanie kodu na kliknięcie w przycisk "TAK, PRZENOSZĘ" w odpowiedzi na pytanie "Czy chcesz przenieść z innej instytucji finansowej?" na stronach:
* inpzu.pl/tfi/ikze-wniosek
* inpzu.pl/tfi/ike-wniosek

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/09073a89-3cd6-471a-bf9c-cdce73c7f764)

``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_TAK",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, np. "Tak, przenoszę IKE" lub "Tak, przenoszę IKZE"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, czyli "Czy chcesz przenieść IKE z innej instytucji finansowej?" lub "Czy chcesz przenieść IKZE z innej instytucji finansowej?"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, czyli np: "IKE" lub "IKZE"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "IKZE"
  "step": "0a"
});
```

### 4) wybór odpowiedzi "NIE, NIE PRZENOSZĘ" na formularzu
Prośba o wywołanie kodu na kliknięcie w przycisk "NIE, NIE PRZENOSZĘ" w odpowiedzi na pytanie "Czy chcesz przenieść z innej instytucji finansowej?" na stronach:
* inpzu.pl/tfi/ikze-wniosek
* inpzu.pl/tfi/ike-wniosek

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/09073a89-3cd6-471a-bf9c-cdce73c7f764)

``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_NIE",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, np. "NIE, NIE PRZENOSZĘ"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, czyli "Czy chcesz przenieść IKE z innej instytucji finansowej?" lub "Czy chcesz przenieść IKZE z innej instytucji finansowej?"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, czyli np: "IKE" lub "IKZE"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "IKZE"
  "step": "0a"
});
```

### 5) kliknięcie w przycisk "KUP"
Prośba o wywołanie kodu na kliknięcie w przycisk "KUP" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/eb92f011-40ea-42de-be33-3b37632d3e09)

``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_KUP",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "KUP"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, np. "Wybierz fundusze do IKE", "Karta funduszy indeksowych"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "IKE", "Portfel Obligacyjny"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Portfel modelowy"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```

### 6) kliknięcie w przycisk "DOWIEDZ SIĘ WIĘCEJ"
Prośba o wywołanie kodu na kliknięcie w przycisk "DOWIEDZ SIĘ WIĘCEJ" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/5ece964a-7ea3-4ae9-9d1a-aa1387a0b2e8)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_WIECEJ",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "DOWIEDZ SIĘ WIĘCEJ"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, np. "Wybierz fundusze do IKE", "Poznaj nasze portfele modelowe"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "Portfel Obligacyjny"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Portfel modelowy"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```

### 7) kliknięcie w przycisk "dodaj do porównania"
Prośba o wywołanie kodu na kliknięcie w przycisk "dodaj do porównania" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/0ad892d0-e9cf-4ecd-a523-f310adbddd09)

``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_POROWNAJ",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "dodaj do porównania"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, np. "Wybierz fundusze do IKE", "Fundusze indeksowe i cyklu życia"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```

### 8) kliknięcie w przycisk z nazwą produktu
Prośba o wywołanie kodu na kliknięcie w przycisk z nazwą produktu na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/0792f7f3-56bc-4873-9cb5-38a60fb88b7f)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_PRODUKT",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, np "inPZU Puls Życia 2025"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, np. "Wybierz fundusze do IKE", "Fundusze indeksowe i cyklu życia"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```

### 9) kliknięcie w przycisk "PODAJ KWOTĘ"
Prośba o wywołanie kodu na kliknięcie w przycisk "PODAJ KWOTĘ" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/3bbb685d-56f6-4da2-b89f-a11b6787c331)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_KWOTA",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "PODAJ KWOTĘ"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, np. "Wybierz fundusze do IKE", "Fundusze indeksowe i cyklu życia"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```

### 10) kliknięcie w przycisk "DODAJ"
Prośba o wywołanie kodu na kliknięcie w przycisk "DODAJ" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/6637a7f8-8d9a-4f58-a07b-f26b18e72b7f)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_DODAJ",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "DODAJ"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, tu "Podaj kwotę"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```


### 11) kliknięcie w przycisk "POTWIERDŹ I PRZEJDŹ DO WERYFIKACJI TOŻSAMOŚCI"
Prośba o wywołanie kodu na kliknięcie w przycisk "POTWIERDŹ I PRZEJDŹ DO WERYFIKACJI TOŻSAMOŚCI" na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/c632b293-ca99-42b0-8064-1e93a8e2cd61)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_POTWIERDZ",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "POTWIERDŹ I PRZEJDŹ DO WERYFIKACJI TOŻSAMOŚCI"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, tu "Sprawdź podsumowanie"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```


### 12) kliknięcie w przycisk "GOTOWE"
Prośba o wywołanie kodu na kliknięcie w przycisk "GOTOWE" po poprawnym zatwierdzeniu kodu sms na stronach ze ścieżką, gdzie przycisk jest dostępny

![image](https://github.com/idgagroupone/PZU-TFI/assets/171781719/f503928f-b20e-484a-99a1-409889af506e)


``` javascript
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "click_button_GOTOWE",
  "click_text": "[NAZWA TEKSTU]", //zmienna przekazująca kliknięty tekst, tu "GOTOWE"
  "section": "[NAZWA SEKCJI]", // zmienna przekazująca nazwę sekcji, tu "Sprawdź podsumowanie"
  "product": "[NAZWA PRODUKTU]", // zmienna przekazująca nazwę produktu, którego dotyczy wybrana ścieżka, np: "inPZU Puls Życia 2025", "PZU Globalny Obligacji Korporacyjnych"
  "brand": "[NAZWA BRANDU]", // zmienna przekazująca nazwę brandu, którego dotyczy wybrana ścieżka np: "IKE" lub "Fundusze indeksowe i cyklu życia"
  "category": [NAZWA KATEGORII PRODUKTU], // zmienna przekazująca nazwę kategorii produktu, którego dotyczy wybrana ścieżka, np. "Fundusz Cyklu Życia", "Fundusz indeksowy"
  "step": "[krok ścieżki"] // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany
});
```


New File at / · idgagroupone/PZU-TFI

