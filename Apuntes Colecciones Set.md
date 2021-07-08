
COLECCIONES SET
_______________
Ventajas:

No permiten elementos duplicados
Uso sencillo del método add que además asegura no elementos duplicados

Inconvenientes:

No tienen acceso aleatorio
Poca eficiencia a la hora de ordenar elementos(Y no siempre se puede)

Tipos:

HashSet
LinkedHasSet
TreeSet
EnumSet
CopyOnWriteArraySet
ConcurrentSkeipListSet


HASHSET(); 

Características de HashSet:
Implementa la interface Set.
La estructura de datos subyacente para HashSet es hashtable.
A medida que implementa la interfaz de configuración, no se permiten valores duplicados.
No se garantiza que los objetos que inserte en HashSet se inserten en el mismo orden.Los objetos se insertan en función de su código hash.
Se permiten elementos NULL en HashSet.
HashSet también implementa interfaces serializables y clonables.
Usando HashSet
Para crear un HashSet solo tenemos que definirlo del siguiente modo:

HashSet<String> hashSet = new HashSet<String>();
Parece simple pero en realidad si echamos un vistazo un poco más allá veremos que el código refiere al siguiente constructor de ejemplo:

public HashSet() {
       map = new HashMap<>();
   }
Ahora es cuando podemos entender la relación directa entre un HashSet, que implementa la interfaz Set, y HashMap que implementa la interface Map. Tal como mencionamos al comienzo del artículo un HashSet no permite objetos repetidos y en su momento el equipo de desarrollo de Java decidieron, para asegurarse de que no pudiéramos ingresar objetos repetidos, decidió utilizar un HashMap internamente el cual tampoco permite la repetición de objetos. Aunque confuso, es una solución que funciona y permite reutilizar su código. Y si algo funciona ¿para qué tocarlo?.

Ejemplo de uso de HashSet:
import java.util.HashSet;
public class HashSetExample {
   public static void main(String args[]) {
      // HashSet declaration
      HashSet<String> hset = 
               new HashSet<String>();

      // Adding elements to the HashSet
      hset.add("Apple");
      hset.add("Mango");
      hset.add("Grapes");
      hset.add("Orange");
      hset.add("Fig");

      //Addition of duplicate elements
      hset.add("Apple");
      hset.add("Mango");

      //Addition of null values
      hset.add(null);
      hset.add(null);

      //Displaying HashSet elements
      System.out.println(hset);
    }
}
Salida:

[null, Mango, Grapes, Apple, Orange, Fig]
 
  
  LINKEDHASHSET(),TREESET() Y HASHSET()
  _____________________________________
  
  Hashset vs Linkedhashset
Otra de las clase utilizada con frecuencia es LinkedHashSet, básicamente una versión ordenada de HashSet que mantiene una lista doblemente vinculada en todos los elementos. Su uso es recomendado cuando necesitamos mantener el orden de iteración elementos que la componen dado que como habíamos comentado HashSet no garantiza su orden de inserción.

En cuanto al rendimiento y velocidad, la clase más rápida es HashSet aunque tanto HashSet y LinkedHashSet ofrecen un rendimiento de tiempo constante.

Otra de las clases a tener en cuenta es TreeSet que junto con las anteriores forman en Java son implementaciones para la colección y almacenaje de objetos. La característica principal de TreeSet es la clasificación, mientras que LinkedHashSet es el orden de inserción y HashSet es solo una colección de propósito general para almacenar objetos.

Dicho esto, quizá la mejor forma de entender su funcionamiento y características es mediante un ejemplo:

// Java program to demonstrate difference between 
// HashSet, LinkedHashSet and TreeSet 
// according to insertion order and insertion time 
  
import java.util.Arrays; 
import java.util.HashSet; 
import java.util.LinkedHashSet; 
import java.util.TreeSet; 
  
class GFG1 { 
    // Function show insertion order of LinkedHashSet, TreeSet and HashSet 
  
    private static void insertionOrder() 
    { 
        LinkedHashSet<String> geekLinkSet 
            = new LinkedHashSet<>(); 
        TreeSet<String> geekTreeSet 
            = new TreeSet<>(); 
        HashSet<String> geekHashSet 
            = new HashSet<String>(); 
  
        // Add three object in 
        // LinkedHashSet and TreeSet 
        for (String str : Arrays.asList("Geek2", 
                                        "Geek1", 
                                        "Geek3", 
                                        "Geek1")) { 
  
            geekLinkSet.add(str); 
            geekTreeSet.add(str); 
            geekHashSet.add(str); 
        } 
  
        // should be sorted order HashSet 
        // stores element in sorted order 
        System.out.println("Insertion Order"
                           + " of objects in HashSet :"
                           + geekHashSet); 
  
        // insertion order or elements LinkedHashSet 
        // storeds elements as insertion 
        System.out.println("Insertion Order of "
                           + "objects in LinkedHashSet :"
                           + geekLinkSet); 
  
        // should be sorted order TreeSet 
        // stores element in sorted order 
        System.out.println("Insertion Order of"
                           + " objects in TreeSet :"
                           + geekTreeSet); 
    } 
  
    // Function calculate insertion time of 
    // 1000 objects of LinkedHashSet, 
    // TreeSet and HashSet 
  
    private static void insertionTime() 
    { 
        // HashSet performance Test 
        // inserting 1000 elements 
        HashSet<Integer> numbersHS 
            = new HashSet<>(); 
        long startTime 
            = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            numbersHS.add(i); 
        } 
        long endTime = System.nanoTime(); 
        System.out.println("Total time to insert"
                           + " 1000 elements in"
                           + " HashSet in sec : "
                           + (endTime - startTime)); 
  
        // LinkedHashSet performance Test 
        // inserting 1000 elements 
        LinkedHashSet<Integer> numbersLLS 
            = new LinkedHashSet<>(); 
  
        startTime = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            numbersLLS.add(i); 
        } 
        endTime = System.nanoTime(); 
        System.out.println("Total time to insert"
                           + " 1000 elements in"
                           + " LinkedHashSet in sec : "
                           + (endTime - startTime)); 
  
        // TreeSet performance Test inserting 1000 objects 
        TreeSet<Integer> numbersTS = new TreeSet<>(); 
  
        startTime = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            numbersTS.add(i); 
        } 
        endTime = System.nanoTime(); 
        System.out.println("Total time to insert"
                           + " 1000 elements in"
                           + " TreeSet in sec : "
                           + (endTime - startTime)); 
    } 
  
    // Function calculate deletion time 
    // of 1000 objects LinkedHashSet, 
    // TreeSet and HashSet 
    // Deletion time always vary 
    private static void deletion() 
    { 
        // HashSet performance Test inserting 
        // and deletion 1000 elements 
        HashSet<Integer> deletionHS 
            = new HashSet<>(); 
  
        for (int i = 0; i < 1000; i++) { 
            deletionHS.add(i); 
        } 
  
        long startingTime = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            deletionHS.remove(i); 
        } 
  
        long endedTime = System.nanoTime(); 
        System.out.println("Total time to Deletion "
                           + "1000 elements in HashSet in sec : "
                           + Math.abs(startingTime - endedTime)); 
  
        // LinkedHashSet  performance Test inserting 
        // and deletion 1000 elements 
        LinkedHashSet<Integer> deletionLLS 
            = new LinkedHashSet<>(); 
  
        for (int i = 0; i < 1000; i++) { 
            deletionLLS.add(i); 
        } 
        startingTime = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            deletionLLS.remove(i); 
        } 
  
        endedTime = System.nanoTime(); 
        System.out.println("Total time to Deletion 1000"
                           + " elements in LinkedHashSet in sec : "
                           + Math.abs(startingTime - endedTime)); 
  
        // TreeSet performance Test inserting 
        // and deletion 1000 elements 
        TreeSet<Integer> deletionTS 
            = new TreeSet<>(); 
  
        for (int i = 0; i < 1000; i++) { 
            deletionTS.add(i); 
        } 
  
        startingTime = System.nanoTime(); 
        for (int i = 0; i < 1000; i++) { 
            deletionTS.remove(i); 
        } 
  
        endedTime = System.nanoTime(); 
        System.out.println("Total time to Deletion 1000"
                           + " elements in TreeSet in sec : "
                           + Math.abs(startingTime - endedTime)); 
    } 
  
    public static void main(String args[]) 
    { 
  
        insertionOrder(); 
        insertionTime(); 
        deletion(); 
    } 
} 
 

Si todo es correcto la salida debe ser la siguiente:

Insertion Order of objects in HashSet :[Geek3, Geek2, Geek1]
Insertion Order of objects in LinkedHashSet :[Geek2, Geek1, Geek3]
Insertion Order of objects in TreeSet :[Geek1, Geek2, Geek3]
Total time to insert 1000 elements in HashSet in sec : 3752794
Total time to insert 1000 elements in LinkedHashSet in sec : 1293794
Total time to insert 1000 elements in TreeSet in sec : 8073353
Total time to Deletion 1000 elements in HashSet in sec : 848690
Total time to Deletion 1000 elements in LinkedHashSet in sec : 937622
Total time to Deletion 1000 elements in TreeSet in sec : 3346092
Como conclusión, tanto HashSet, LinkedHashSet y TreeSet nos permiten poder trabajar de manera eficiente con nuestra colección de objetos en Java, cada uno con sus pros y contras. A modo introducción en este artículo hemos aprendido sus fundamentos y método de uso. En próximos artículos iremos profundizando un poco más en su utilización. Por el momento si tienes cualquier duda deja tu comentario y si te ha gustado este artículo no dudes en compartirlo en tus redes sociales.

