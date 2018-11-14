---
title: Exceptions et déroulement de pile en C++
ms.date: 11/04/2016
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 5e094101557469a189311ce2c5344bb895696649
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330946"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Exceptions et déroulement de pile en C++

Dans le mécanisme d'exception C++, le contrôle passe de l'instruction Throw à la première instruction Catch qui peut gérer le type levé. Lorsque l’instruction catch est atteinte, toutes les variables automatiques qui sont dans la portée entre la levée et l’instruction catch sont détruites dans un processus connu sous le nom *de déroulement de pile*. L'exécution du déroulement de pile se déroule comme suit :

1. Le contrôle atteint la **essayez** instruction par une exécution séquentielle normale. La section protégée dans le **essayez** bloc est exécuté.

1. Si aucune exception n’est levée pendant l’exécution de la section protégée, la **catch** clauses qui suivent le **essayez** bloc ne sont pas exécutées. L’exécution se poursuit à l’instruction après le dernier **catch** clause qui suit associé **essayez** bloc.

1. Si une exception est levée pendant l’exécution de la section protégée ou dans toute routine de la section protégée appelle directement ou indirectement, un objet exception est créé à partir de l’objet qui est créé par le **lever** opérande. (Cela implique qu'un constructeur de copie peut être concerné.) À ce stade, le compilateur recherche un **catch** clause dans un contexte d’exécution plus élevé qui peut gérer une exception du type qui est levé, ou pour un **catch** gestionnaire qui peut gérer tout type d’exception. Le **catch** gestionnaires sont examinés dans leur ordre d’apparition après le **essayez** bloc. Si aucun gestionnaire approprié n’est trouvé, l’englobant dynamique suivant qui **essayez** bloc est examiné. Ce processus se poursuit jusqu'à ce que l’englobant le plus éloigné **essayez** bloc est examiné.

1. Si aucun gestionnaire correspondant ne parvient à être trouvé, ou si une exception se produit pendant le processus de déroulement mais avant que le gestionnaire n'obtienne le contrôle, la fonction runtime `terminate` prédéfinie est appelée. Si une autre exception se produit après la levée de l'exception mais avant le début du déroulement, la fonction `terminate` est appelée.

1. Si une correspondance **catch** gestionnaire est trouvé et il intercepte par valeur, son paramètre formel est initialisé en copiant l’objet exception. Si l'interception s'effectue par référence, le paramètre est initialisé pour faire référence à l'objet exception. Une fois le paramètre formel initialisé, le processus de déroulement de la pile démarre. Cela implique la destruction de tous les objets automatiques qui ont été entièrement construits — mais pas encore détruits, entre le début de la **essayez** bloc qui est associé le **catch** gestionnaire et le lever le site de l’exception. La destruction se produit dans l'ordre inverse de la construction. Le **catch** gestionnaire est exécuté et le programme reprend son exécution après le dernier gestionnaire, autrement dit, lors de la première instruction ou construction qui n’est pas un **catch** gestionnaire. Contrôle ne peut entrer un **catch** gestionnaire via une exception levée, jamais via un **goto** instruction ou un **cas** étiquette dans un **commutateur** instruction.

## <a name="stack-unwinding-example"></a>Exemple de déroulement de pile

L'exemple suivant illustre le déroulement de la pile lorsqu'une exception est levée. L'exécution sur le thread passe de l'instruction Throw dans `C` à l'instruction Catch dans `main` et déroule chaque fonction pendant le processus. Notez l’ordre dans lequel les objets `Dummy` sont créés puis détruits lorsqu’ils passent hors de portée. Notez également qu'aucune fonction ne se termine, sauf `main`, qui contient l'instruction Catch. La fonction `A` ne retourne jamais d'un appel à `B()`, et `B` ne retourne jamais d'un appel à `C()`. Si vous supprimez les marques de commentaire de la définition du pointeur `Dummy` et de l'instruction Delete correspondante et que vous exécutez le programme, le pointeur n'est jamais supprimé. Cela indique ce qui peut se produire lorsque les fonctions ne fournissent pas de garantie d'exception. Pour plus d'informations, consultez Comment : concevoir des exceptions. Si vous commentez l'instruction Catch, vous pouvez observer ce qui se produit lorsqu'un programme se termine en raison d'une exception non gérée.

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```