Савенко Д.В., <ds@dsavenko.com>

# Паттерн проектирования «Стратегия» (Strategy)

## Задание

1. Создайте интерфейс `Converter` с методом `String convert(int x)`, сделайте две реализации — одна просто переводит число в строку, вторая — в строку в римской записи, реализацию можете взять отсюда
	```Java
	import java.util.TreeMap;

	public class RomanNumber {

	    private final static TreeMap<Integer, String> map = new TreeMap<Integer, String>();

	    static {

	        map.put(1000, "M");
	        map.put(900, "CM");
	        map.put(500, "D");
	        map.put(400, "CD");
	        map.put(100, "C");
	        map.put(90, "XC");
	        map.put(50, "L");
	        map.put(40, "XL");
	        map.put(10, "X");
	        map.put(9, "IX");
	        map.put(5, "V");
	        map.put(4, "IV");
	        map.put(1, "I");

	    }

	    public final static String toRoman(int number) {
	        int l =  map.floorKey(number);
	        if ( number == l ) {
	            return map.get(number);
	        }
	        return map.get(l) + toRoman(number-l);
	    }

	}
	```
2. Создайте класс `IntegerPrinter` с методом `void print(int x)`. Этот класс получает в конструкторе файл, куда писать, и конвертер. Метод `print()` пишет переданное число в файл, используя конвертер.
3. Запишите числа от 1 до 1000 в два файла — в арабской и римской записи.

## Требования

1. (**обязательно**) Обеспечьте разделение кода на модель и UI средствами ООП и Java (пакеты, классы, интерфейсы, и т.д.).
2. Корректно обработайте возможные ошибки (исключения).
3. Старайтесь не нарушать принципов ООП и объектного дизайна.
4. Старайтесь обеспечить хороший уровень инкапсуляции (т.е. выявлять самостоятельные сущности в задачах и заключать их в отдельные классы и, при необходимости, выделять их интерфейсы, обеспечивать сокрытие данных и логики с помощью приватных полей классов и пакетной видимости классов, где применимо, и т.д.).