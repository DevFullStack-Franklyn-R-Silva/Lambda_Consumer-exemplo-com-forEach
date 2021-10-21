# Consumer (exemplo com forEach)
Consumer https://docs.oracle.com/javase/10/docs/api/java/util/function/Consumer.html

```java
public interface Consumer<T> {
    void accept(T t);
}
```
## Problema exemplo
Fazer um programa que, a partir de uma lista de produtos, aumente o
preço dos produtos em 10%.
```java
    List<Product> list = new ArrayList<>();

    list.add(new Product("Tv", 900.00));
    list.add(new Product("Mouse", 50.00));
    list.add(new Product("Tablet", 350.50));
    list.add(new Product("HD Case", 80.90));
```
## Versões:
• Implementação da interface

• Reference method com método estático

• Reference method com método não estático

• Expressão lambda declarada

• Expressão lambda inline

### Implementação da interface
```java
list.forEach(new PriceUpdate());

list.forEach(System.out::println);
```

```java
import java.util.function.Consumer;

import entities.Product;

public class PriceUpdate implements Consumer<Product>{

	@Override
	public void accept(Product p) {
		p.setPrice(p.getPrice() * 1.1);
	}
}
```
### Reference method com método estático
```java
public static void staticPriceUpdate(Product p) {
		p.setPrice(p.getPrice() * 1.1);
}
```

```java
list.forEach(Product :: staticPriceUpdate);
```
### Reference method com método não estático
```java
public void nonStaticPriceUpdate() {
		price = price * 1.1;
}
```

```java
list.forEach(Product :: nonStaticPriceUpdate);
```
### Expressão lambda declarada
```java
double factor = 1.1;
Consumer<Product> cons = p -> p.setPrice(p.getPrice() * factor); 
```
### Expressão lambda inline
```java
double factor = 1.1;
list.forEach(p -> p.setPrice(p.getPrice() * factor));
```
