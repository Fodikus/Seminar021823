# Seminar021823
Домашняя работа №7 к семинару "Знакомство с языками программирования"

Задача 47. Задайте двумерный массив размером m×n, заполненный случайными вещественными числами.
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

  void CheckOddPosition(int[,] matrix, double[] array)
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
  CheckOddPosition(matrix, array);

  Console.WriteLine($"Среднее арифметическое каждого столбца:  [{string.Join(", ", array)}]");
```

# Транспонирование.
```

```

# Миша и негатив.
```

```

# Заполнение диагональю.
```

```
