# Seminar021823
Домашняя работа №7 к семинару "Знакомство с языками программирования"

# Задача 47. Задайте двумерный массив размером m×n, заполненный случайными вещественными числами.
```
void InputMatrix(double[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(-10*100, 10*100)/100.0;
    }
}

void PrintMatrix(double[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
double[,] matrix = new double[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
```

# Задача 50. Напишите программу, которая на вход принимает позиции элемента в двумерном массиве, и возвращает значение этого элемента или же указание, что такого элемента нет.
```
void InputMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(-10, 10);
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
int[,] matrix = new int[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
Console.Write("Введите позицию массива: ");
int[] poz = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();

if (poz[0] < 0 || poz[0] > matrix.GetLength(0)-1 || poz[1] < 0 || poz[1] > matrix.GetLength(1)-1)
{
    Console.WriteLine($"{poz[0]}, {poz[1]} -> Такой позиции в массиве нет");
}
else
{
    Console.WriteLine($"{poz[0]}, {poz[1]} -> {matrix[poz[0], poz[1]]}");
}
```

# Задача 52. Задайте двумерный массив из целых чисел. Найдите среднее арифметическое элементов в каждом столбце.
```
void InputMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(0, 9);
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

void SummAverage(int[,] matrix, double[] array)
{
    for (int j = 0; j < matrix.GetLength(1); j++)
    {
        double summ = 0;

        for (int i = 0; i < matrix.GetLength(0); i++)
        {
            summ = summ + matrix[i, j];

        }

        array[j] = array[j] + Math.Round(summ/matrix.GetLength(0), 2);
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
int[,] matrix = new int[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
double[] array = new double[matrix.GetLength(1)];
SummAverage(matrix, array);

Console.WriteLine($"Среднее арифметическое каждого столбца:  [{string.Join(", ", array)}]");
```

# Транспонирование(https://acmp.ru/asp/do/index.asp?main=task&id_course=1&id_section=8&id_topic=120&id_problem=745).
```
void InputMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(0, 100);
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

void Shift(int[,] matrix,int[,] result)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            result[matrix.GetLength(0) - i - 1, j] = matrix[i, j];
        }
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
int[,] matrix = new int[size[0], size[1]];
int[,] result = new int[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
Shift(matrix,result);
Console.WriteLine("Массив после Транспонирования:");
PrintMatrix(result);
```

# Миша и негатив(https://acmp.ru/asp/do/index.asp?main=task&id_course=1&id_section=8&id_topic=121&id_problem=749).
```
void InputMatrix(char[,] matrix)
{
    int symbol = 0;
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            symbol = new Random().Next(0, 2);
            if (symbol == 1)
                matrix[i, j] = 'W';
            else
                matrix[i, j] = 'B';
        }    
    }
}

void PrintMatrix(char[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

int CheckPosition(char[,] matrix,char[,] result)
{
    int check = 0;
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            if(matrix[i,j] == result[i,j])
                check++;
        }
    }

    return check;
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
char[,] matrix = new char[size[0], size[1]];
char[,] result = new char[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
Console.WriteLine("");
InputMatrix(result);
PrintMatrix(result);

int check = CheckPosition(matrix,result);
Console.Write($"Неправильно сформированых символов: {check}");
```

# Заполнение диагональю.
```
void InputMatrix(int[,] matrix)
{
    int number = 1;
    if (matrix.GetLength(0) == matrix.GetLength(1))
    {
        for (int i = 1-matrix.GetLength(0); i <= matrix.GetLength(0)-1; i++)
        {
            for (int j = 0; j < matrix.GetLength(1); j++)
            {
                int k = j - i;
                if (k < 0 || k >= matrix.GetLength(1))
                    continue;

                matrix[j, matrix.GetLength(1)-k-1] = number++;
            }
        }
    }
    else if (matrix.GetLength(0) > matrix.GetLength(1))
    {
        int r = matrix.GetLength(0) - matrix.GetLength(1);
        for (int i = 1-matrix.GetLength(0); i <= matrix.GetLength(0)-1; i++)
        {
            for (int j = 0; j < matrix.GetLength(1) + r; j++)
            {
                int k = j - i;
                if (k < 0 || k >= matrix.GetLength(1))
                    continue;

                matrix[j, matrix.GetLength(1)-k-1] = number++;
            }
        }
    }
    else
    {
        int r = matrix.GetLength(1) - matrix.GetLength(0);
        for (int i = 1-matrix.GetLength(0); i < matrix.GetLength(0)+r; i++)
        {
            for (int j = 0; j < matrix.GetLength(1)-r; j++)
            {
                int k = j - i + r;

                if (k < 0 || k >= matrix.GetLength(1))
                {
                    continue;
                }

                matrix[j, matrix.GetLength(1)-k-1] = number++;
            }
        }
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");
int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
int[,] matrix = new int[size[0], size[1]];
Console.WriteLine("Двумерный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
```
