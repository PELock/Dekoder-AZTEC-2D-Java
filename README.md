#Dekoder Kodu AZTEC 2D z Dowodu Rejestracyjnego dla Java

Oferujemy Państwu usługę Web API pozwalającą zdekodować dane z kodu AZTEC 2D zapisanego w dowodach rejestracyjnych pojazdów samochodowych.

![Kod AZTEC 2D zapisany w formie obrazkowej w dowodzie rejestracyjnym pojazdu](https://www.pelock.com/img/pl/produkty/dekoder-aztec/dowod-rejestracyjny-kod-aztec-2d.jpg)

Nasza biblioteka dekoduje dane z dowodu rejestracyjnego, zapisane w postaci kodu obrazkowego tzw. kod aztec. Dekodowane są wszystkie wymienione pola w dowodzie rejestracyjnym pojazdu.

https://www.pelock.com/pl/produkty/dekoder-aztec

##Gdzie znajdzie zastosowanie Dekoder AZTec?

Dekoder AZTec może przydać się firmom i instytucjom, które pragną zautomatyzować proces ręcznego wprowadzania danych z dowodów rejestracyjnych i zastąpić go poprzez wykorzystanie naszej biblioteki programistycznej, która potrafi rozpoznać i rozkodowac kody AZTEC 2D bezpośrednio ze zdjęć dowodów rejestracyjnych lub zeskanowanych już kodów (wykorzystując skaner QR / AZTEC 2D).

##Dostępne edycje programistyczne

Dekoder AZTec dostepny jest w trzech edycjach. Każda wersja posiada inne cechy i inne możliwości dekodowania. Wersja oparta o Web API jako jedyna posiada możliwość rozpoznawania i dekodowania danych bezpośrednio ze zdjęć i obrazków. Pozostałe wersje do dekodowania wymagają już odczytanego kodu w postaci tekstu (np. ze skanera).

![Dekodowanie kodu AZTEC 2D do formatu JSON](https://www.pelock.com/img/pl/produkty/dekoder-aztec/dekodowanie-kodu-aztec-2d-do-json.png)

###Wersja Web API

Jest to najbardziej zaawansowana edycja Dekodera AZTec, ponieważ umożliwia precyzyjne rozpoznawanie i dekodowanie kodów AZTEC 2D bezpośrednio ze zdjęć oraz obrazków zapisanych w formatach PNG lub JPG.

Algorytm rozpoznawania obrazu należy do naszej firmy, jest to innowacyjne rozwiązanie rozwijane od podstaw przez prawie rok czasu.

Rozumiemy potrzeby naszych klientów oraz problemy wynikające z rozpoznawnia rzeczywistych zdjęć kodów AZTEC 2D znajdujących się w dowodach rejestracyjnych, które nie zawsze są idealnie wykonane, czy to ze względu na rodzaj aparatu, kąta wykonania zdjęcia, refleksów czy słabej rozdzielczości.

Przy tworzeniu naszego rozwiązania wzieliśmy wszystkie te czynniki pod uwagę i w efekcie nasz algorytm radzi sobie znakomicie z rozpoznawaniem kodów AZTEC 2D ze zdjęć z wszelkiego rodzaju zniekształceniami, uszkodzeniami i niedoskonałościami. Znacznie przewyższa pod względem funkcjonowania dostępne na rynku biblioteki rozpoznawnia kodów AZTEC 2D takie jak np. ZXing.

####Instalacja

Preferowany sposób instalacji biblioteki poprzez zależności [maven](https://mvnrepository.com/).

####Użycie dekodera AZTEC 2D w Java

```java
//
// załącz klasę dekodera
//
import com.pelock.AZTecDecoder;
import org.json.JSONObject;

public static void main(String[] args)
{
	// utwórz klasę dekodera (używamy naszego klucza licencyjnego do inicjalizacji)
	AZTecDecoder myAZTecDecoder = new AZTecDecoder("ABCD-ABCD-ABCD-ABCD");

	//
	// 1. Dekoduj dane bezpośrednio z pliku graficznego, zwróć wynik jako tablicę
	//
	JSONObject DecodedArray = myAZTecDecoder.DecodeImageFromFile("C:\\zdjecie-dowodu.jpg");

	// czy udało się zdekodować dane?
	if (DecodedArray != null && (Boolean)DecodedArray.get("Status") == true)
	{
		// wyświetl rozkodowane dane (są zapisane jako tablica asocjacyjna)
		System.out.println(DecodedArray.toString(4));
	}

	//
	// 2. Dekoduj dane bezpośrednio z pliku graficznego i zwróć wynik jako string JSON
	//
	JSONObject DecodedJSON = myAZTecDecoder.DecodeImageFromFile("C:\\zdjecie-kodu-aztec-2d.png");

	if (DecodedJSON != null)
	{
		System.out.println(DecodedJSON.toString(4));
	}

	//
	// 3. Dekoduj dane z odczytanego już ciągu znaków (np. wykorzystując skaner ręczny)
	//
	// zakodowane dane z dowodu rejestracyjnego
	String szValue = "ggMAANtYAAJD...";

	JSONObject DecodedText = myAZTecDecoder.DecodeText(szValue);

	if (DecodedText != null)
	{
		System.out.println(DecodedText.toString(4));
	}

	//
	// 4. Dekoduj dane z odczytanego już ciągu znaków zapisanego w pliku (np. wykorzystując skaner ręczny)
	//
	JSONObject DecodedTextFile = myAZTecDecoder.DecodeTextFromFile("C:\\odczytany-ciag-znakow-aztec-2d.txt");

	if (DecodedTextFile != null)
	{
		System.out.println(DecodedTextFile.toString(4));
	}
}
```

Bartosz Wójcik
https://www.pelock.com | http://www.dekoderaztec.pl