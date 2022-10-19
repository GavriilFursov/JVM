public class JvmComprehension {

    public static void main(String[] args) { инициализация JvmComprehension, main попадает в stack;
        int i = 1;                      // 1 В фрейме main в стеке создали примитив int i = 1;
        Object o = new Object();        // 2 Object попадает в кучу (heap);
        Integer ii = 2;                 // 3 Integer загружается ClassLoader’ом, ii - stack, new Integer в heap;
        printAll(o, i, ii);             // 4 printAll и его сигнатуры - stack; В его фрейме примитив i и ссылки на obj o and ii, Object and Integer located in heap; 
        System.out.println("finished"); // 7 println попадает в stack, принимает ссылку на объект в куче, со значение finished; 
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 В стеке создали переменную uselessVar, которая ссылается на объект Integer в куче, принимает значение 700, созданный во frame printAll;
        System.out.println(o.toString() + i + ii);  // 6 В стеке создали фрейм println и примитив i, принимает ссылку на obj i ann ii, находится в куче и принимает значение i;
    }
}