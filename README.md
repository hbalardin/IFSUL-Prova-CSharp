Aluno: Henrique Balardin
Turma: 4INF
Ano: 2022

# IFSUL-Prova-CSharp
Prova da disciplina de Linguagem de Programação III.

## 1) Escreva  um  programa  que  leia  três  valores  para os  lados  de  um  triângulo  (variáveis  A,  B  e  C).  Verificar  se  cada lado é menor que a soma dos outros dois lados. Se sim, saber de A==B e se B==C, sendo verdade o triângulo é equilátero;  Se  não,  verificar  de  A==B  ou  se  A==C  ou  se  B==C,  sendo  verdade  o  triângulo  é  isósceles;  e caso contrário,  o  triângulo  será  escaleno.  Caso  os  lados  fornecidos  não  caracterizarem  um  triângulo,  avisar  a ocorrência.

```C#
using System;

namespace Triangle{
	public class Program
	{
		public static void Main()
		{
			Selector();
		}
		
		public static void Selector(){
			Console.WriteLine("===== Identificador de triângulo! =====");
			
			Console.WriteLine("Digite o valor de um lado do triângulo: ");
			double a = double.Parse(Console.ReadLine());
			
			Console.WriteLine("Digite o valor do outro lado do triângulo: ");
			double b = double.Parse(Console.ReadLine());
			
			Console.WriteLine("Digite o valor do último lado do triângulo: ");
			double c = double.Parse(Console.ReadLine());
			
			if (!IsEachSideLowerThanOtherSidesSum(a, b, c)){
				Console.WriteLine("Triângulo Inválido: ");
				return;
			}
			if (IsEquilateralTriangle(a, b, c)){
				Console.WriteLine("Triângulo Equilátero: ");
				return;
			}
			if (IsIsosceles(a, b, c)){
				Console.WriteLine("Triângulo Isósceles: ");
				return;
			}
			Console.WriteLine("Triângulo Escaleno: ");
		}
		
		public static bool IsEachSideLowerThanOtherSidesSum(double a, double b, double c){
			if (a > b + c) return false;
			if (b > a + c) return false;
			if (c > a + b) return false;
			return true;
		}
		public static bool IsEquilateralTriangle(double a, double b, double c){
			if (a != b) return false;
			if (b != c) return false;
			return true;
		}
		public static bool IsIsosceles(double a, double b, double c){
			if (a == b) return true;
			if (b == c) return true;
			if (c == a) return true;
			return false;
		}
	}
}
```

## 2) Escrever um programa que leia um conjunto de números positivos, e exiba se o número lido é par ou ímpar. Exiba ao  final  a  soma  total  dos  números  pares  lidos  e  também  a  soma  dos  números  ímpares  lidos.  Suporemos  que  o número de elementos deste conjunto  não é conhecido, e que um número negativo será  utilizado para sinalizar  o fim dos dados.

```C#
using System;

namespace OddsOrEvenCalculator{
	public class Program
	{
		public static void Main()
		{
			Selector();
		}
		
		public static void Selector(){
			Console.WriteLine("===== Calculadora de par ou impar! =====");
			
			int n = 0;
			int oddsSum = 0;
			int evensSum = 0;
			
			while (true){
				Console.WriteLine("Digite um número positivo: ");
				n = int.Parse(Console.ReadLine());
				
				if (n < 0){
					Console.WriteLine();
					Console.WriteLine("A soma dos números pares é: {0}", evensSum);
					Console.WriteLine();
					Console.WriteLine("A soma dos números ímpares é: {0}", oddsSum);
					Console.WriteLine();
					Console.WriteLine("Obrigado pela preferência! ;)");
					Console.WriteLine("====================================================");
					return;
				}

				bool isEven = IsEven(n);

				if (isEven){
					evensSum = Sum(evensSum, n);
				} else {
					oddsSum = Sum(oddsSum, n);
				}
			}
		}
		
		public static bool IsEven(int n){
			return n % 2 == 0;
		}
		public static int Sum(int n1, int n2){
			return n1 + n2; 
		}
	}
}

```

## 3)  Faça um programa que leia 10 valores inteiros e positivos e: 
- Encontre o maior valor 
- Encontre o menor valor 
- Calcule a média dos números lidos.

```C#
using System;

namespace HigherLowerAndAverageNumber{
	public class Program
	{
		public static void Main()
		{
			Selector();
		}
		
		public static void Selector(){
			Console.WriteLine("===== Os 10 números! =====");
			
			int count = 0;
			int higher = 0;
			int lower = 0;
			int total = 0;
			
			while (true){
				count = count + 1;
				
				if (count > 10) {
					Console.WriteLine();
					Console.WriteLine("O maior valor é: {0}", higher);
					Console.WriteLine();
					Console.WriteLine("O menor valor é: {0}", lower);
					Console.WriteLine();
					Console.WriteLine("A média dos valores é: {0}", GetAverage(total, 10));
					Console.WriteLine();
					Console.WriteLine("Obrigado pela preferência! ;)");
					Console.WriteLine("=================================================");
					return;
				};
				
				Console.WriteLine("Digite um número inteiro e positivo: ");
				int n = int.Parse(Console.ReadLine());
				while (n < 0){
					Console.WriteLine("Por digite um número inteiro e positivo válido");
					n = int.Parse(Console.ReadLine());
				}

				higher = GetHigher(higher, n);
				if (count == 1) lower = n;
				else lower = GetLower(lower, n);
				
				total = Sum(total, n);
			}
		}

		public static int GetHigher(int n1, int n2){
			if (n1 > n2) return n1;
			else return n2;
		}
		public static int GetLower(int n1, int n2){
			if (n1 < n2) return n1;
			else return n2;
		}
		public static int Sum(int n1, int n2){
			return n1 + n2; 
		}
		public static double GetAverage(double sum, int divider){
			return sum / divider; 
		}
	}
}
```

## 4) Faça um programa de conversão de base numérica. O programa deverá apresentar uma tela de entrada com as seguintes opções: 1 – Adição 2 – Subtração 3 – Multiplicação 4 – Divisão Informe a opção: A  partir  da  opção  escolhida,  o  programa  deverá  solicitar  para  que  o  usuário  digite  dois  números.  Em  seguida,  o programa  deve  exibir  o  resultado  da  opção  indicada pelo  usuário  e  perguntar  ao  usuário  se  ele  deseja  voltar  ao menu  principal.  Caso  a  resposta  seja   ́S ́  ou   ́s ́,  deverá  voltar  ao  menu,  caso  contrário  deverá  encerrar  o programa.


```C#
using System;

namespace Calculator{
	public class Program
	{
		public static void Main()
		{
			Selector();
		}
		
		public static void Selector(){
			while (true){
				Console.WriteLine("============ Calculadora do Balada =============");
				Console.WriteLine("Escolha uma das opções");
				Console.WriteLine("1 - Adição");
				Console.WriteLine("2 - Subtração");
				Console.WriteLine("3 - Multiplicação");
				Console.WriteLine("4 - Divisão");

				int option = int.Parse(Console.ReadLine());

				while (option < 1 || option > 4){
					Console.WriteLine("Por favor escolha uma opção válida");
					option = int.Parse(Console.ReadLine());
				}

				Console.WriteLine("Digite o primeiro valor");
				double n1 = double.Parse(Console.ReadLine());

				Console.WriteLine("Digite o segundo valor");
				double n2 = double.Parse(Console.ReadLine());

				Console.WriteLine();
				Calc(option, n1, n2);


				Console.WriteLine("Deseja voltar ao menu principal? ");
				char key = Char.Parse(Console.ReadLine());
				bool shouldContinue = ShouldContinue(key);

				if (!shouldContinue) {
					Console.WriteLine();
					Console.WriteLine("Obrigado pela preferência! ;)");
					Console.WriteLine("=================================================");
					return;
				}
			}
		}
		
		public static void Calc(int option, double n1, double n2){
			if (option == 1){
				Sum(n1, n2);
			}
			if (option == 2){
				Subtract(n1, n2);
			}
			if (option == 3){
				Multiply(n1, n2);
			}
			if (option == 4){
				Divide(n1, n2);
			}
		}
		
		public static void Sum(double n1, double n2){
			double result = n1 + n2; 
			Console.WriteLine("O resultado da soma dos dois valores é " + result);
		}
		
		public static void Subtract(double n1, double n2){
			double result = n1 - n2; 
			Console.WriteLine("O resultado da subtração dos dois valores é " + result);
		}
		
		public static void Divide(double n1, double n2){
			double result = n1 / n2; 
			Console.WriteLine("O resultado da divisão dos dois valores é " + result);
		}
		
		public static void Multiply(double n1, double n2){
			double result = n1 * n2; 
			Console.WriteLine("O resultado da multiplicação dos dois valores é " + result);
		}

		public static bool ShouldContinue(char key){
			return Char.Equals(key, 'S') || Char.Equals(key, 's');
		}
	}
}

```
