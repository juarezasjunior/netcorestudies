# Teste Para Analista/Desenvolvedor .NET na Adimax

O objetivo desse teste é ver o seu conhecimento como desenvolvedor .NET e como analista de sistemas.

A maioria das perguntas são dissertativas e desejamos que você coloque o máximo de informações souber.

Não é permitido pesquisar na internet ou por outros meios.

**Bom teste! :)**

## C# - Básico
Nessa seção, temos as perguntas de nível básico da linguagem C#.

#### 1. Escreva tudo o que há de errado no código abaixo:
```
namespace Adimax.MagnusSoftware
{
    using System;

    public class InvoiceItem
    {
        public Invoice()
        {
        }

        public void int CalculateItemCost(quantity, unitPrice)
        {
            return quantity * unitPrice;
        }
    }
}
```
Resposta:


#### 2. No código abaixo, o que são propriedades e o que são campos?
```
namespace Adimax.MagnusSoftware
{
    using System;

    public class OrderItem
    {
        private readonly int orderId;
        private int orderItemId;

        public OrderItem(int orderId)
        {
            this.orderId = orderId;
        }

        public int OrderItemId => this.orderItemId;

        public int ItemId { get; private set; }

        public string ItemName { get; private set; }

        public int Quantity { get; set; }

        public decimal UnitPrice { get; set; }

        public decimal TotalValue => this.Quantity * this.UnitPrice;

        public void NewItem(int itemId, string itemName)
        {
            this.ItemId = this.ItemId;
            this.ItemName = this.ItemName;
        }
    }
}
```
Resposta:


#### 3. Se eu chamar o método WriteNumbers passando o valor de 20, qual será o resultado final da variável number?
```
    public class Writer
    {
        public int WriteNumbers(int number)
        {
            number += 15;

            this.IncrementNumber(number);

            Console.WriteLine("The number is: " + --number);

            return number;
        }

        private int IncrementNumber(int number)
        {
            return number++;
        }
    }
```
Resposta:


#### 4. Como poderíamos melhorar o código da classe abaixo?
```
using System.Collections.Generic;
namespace Adimax.MagnusSoftware
{
    using System;


    public class Invoice
    {
        public void CreateInvoice(int customerId)
        {
            this.customerId = customerId;
        }



        public int customerId;

        public void AddNewItem(int itemId, int quantity, decimal unitPrice)
        {
            InvoiceItem i = new InvoiceItem();

            i.ItemId = itemId;


            i.Quantity = quantity; i.UnitPrice = unitPrice;

            InvoiceItems.Add(i);
        }

        public List<InvoiceItem> InvoiceItems { get; set; }

        public class InvoiceItem
        {
            public int ItemId { get; set; }
            public int Quantity { get; set; }
            public decimal UnitPrice { get; set; }
        }

        public void WriteInvoiceItems()
        {
            Console.WriteLine("This is the invoice for the customer: " + customerId);

            for (int i = 0; i <= InvoiceItems.Count -1; i++)
            {
                string t = "Item: ";

                t = t + InvoiceItems[i].ItemId;

                t = t + " - Quantity: " + InvoiceItems[i].Quantity + 
                " - Total: " + (InvoiceItems[i].Quantity 
                * InvoiceItems[i].UnitPrice).ToString();
                Console.WriteLine("Item: " + t);
            }

        }



    }

    
}
```
Resposta:


## C# - Intermediário
Nessa seção, temos as perguntas de nível intermediário da linguagem C#.

#### 5. Por que as interfaces são importantes? O há de errado no código abaixo?
```
    public interface ICalculator
    {
        int SumNumbers();
    }

    public class Calculator : ICalculator
    {
        public int SumNumbers(int numberA, int numberB)
        {
            return numberA + numberB;
        }
    }
```
Resposta:


#### 6. O que são métodos abstratos e virtuais? Por que o código abaixo não compila?
```
    public abstract class Animal
    {
        public string AnimalName { get; set; }

        public virtual void OnMakesNoises()
        {
            Console.WriteLine("Animal making noises.");
        }

        public abstract string WriteAnimalName();
    }

    public class Dog : Animal
    {
        public override void OnMakesNoises()
        {
            base.OnMakesNoises();

            Console.WriteLine("The dog is barking.");
        }
    }
 ```
Resposta:


#### 7. O que são testes automatizados? Por que eles são importantes? No código abaixo, qual teste vai quebrar? Que teste está faltando para meu código ficar bem validado?
```
    public enum OperatorType
    {
        Sum,
        Multiplication,
    }
    
    public class Calculator
    {
        public int Calculate(
            int numberA,
            int numberB,
            OperatorType operatorType = OperatorType.Multiplication)
        {
            switch (operatorType)
            {
                case OperatorType.Sum:
                    return numberA + numberB;
                case OperatorType.Multiplication:
                    return numberA * numberB;
                default:
                    throw new InvalidOperationException();
            }
        }
    }

    [TestFixture]
    public class CalculatorTests
    {
        [TestCase(20, 2, 40)]
        [TestCase(10, 2, 10)]
        public void MultiplicationTest(int numberA, int numberB, int expectedResult)
        {
            var calculator = new Calculator();

            var result = calculator.Calculate(numberA, numberB, OperatorType.Multiplication);

            Assert.That(result, Is.EqualTo(expectedResult));
        }
    }
```

Resposta:


## C# - Avançado

Nessa seção, temos as perguntas de nível avançado da linguagem C#.

#### 5. Explique o que são params?
```
    public class Calculator
    {
        public int SumNumbers(params int[] numbers)
        {
            var result = 0;

            foreach (var number in numbers)
            {
                result += number;
            }

            return result;
        }
    }
```
Resposta:


#### 8. O que são tuplas? O que o método abaixo irá retornar?
```
    public class Calculator
    {
        public (string message, int result) SumNumbers(int numberA, int numberB)
        {
            var result = numberA + numberB;

            var message = $"The result is: " + result;

            return (message, result);
        }
    }
```
Resposta:


#### 9. O que são Action e Func? Quando utilizamos elas?
Resposta:


#### 10. O que é "the repository pattern"?
Resposta:


#### 11. Para que serve o Entity Framework?
Resposta:


#### 12. O que é injeção de dependência? O que o código do .NET Core abaixo está fazendo?
```
            var serviceProvider = new ServiceCollection()
                .AddLogging(x => x.AddDebug())
                .AddDbContext<MyDbContext>(x => x.UseSqlite("Filename =:memory:"))
                .AddTransient<IInvoiceRepository, InvoiceRepository>()
                .AddTransient<IInvoiceItemRepository, InvoiceItemRepository>()
                .BuildServiceProvider();
```
Resposta:


#### 13. No .NET Core, o que são Middlewares? O que o código abaixo está fazendo?
```
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.UseHttpsRedirection();

            app.UseRouting();

            app.UseAuthorization();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllers();
            });
        }
```
Resposta:


## Analista

Imagine que o seu cliente tenha um sistema que controla o contas a receber da empresa. 

Nesse sistema, o usuário pode cadastrar os clientes da empresa e as contas que eles estão devendo.

Em cada conta, ele informa a data de vencimento e o valor total da conta.

Agora o cliente deseja controlar também as contas a pagar.

Você foi designado para fazer a análise dessa nova funcionalidade.

Escreva abaixo os pontos que você levantou:

**Quais perguntas você faria pra o cliente?**

Resposta:


**Quais são os requisitos da nova funcionalidade?**

Resposta:


**Além do que o cliente pediu, o que a mais poderíamos fazer (além do que ele espera)?**

Resposta:


### Muito obrigado pelas respostas!
