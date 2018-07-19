---
title: Portée (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/08/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8af021120c06465d0fd79ead79e2a18cb593803
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027607"
---
# <a name="scope-c"></a>Portée (C++)

Lorsque vous déclarez un élément de programme comme une classe, une fonction ou une variable, son nom peut uniquement être « vu » et utilisé dans certaines parties de votre programme. Le contexte dans lequel un nom est visible est appelé son *étendue*. Par exemple, si vous déclarez une variable `x` au sein d’une fonction, `x` est uniquement visible dans le corps de la fonction. Il a *portée locale*. Vous pouvez avoir des autres variables portant le même nom dans votre programme ; tant qu’elles se trouvent dans des portées différentes, ils ne violent pas une règle de définitions et aucune erreur n’est générée.

Pour les variables non statiques automatiques, étendue détermine également quand ils sont créés et détruits dans la mémoire programme. 

Il existe six types de portée :

- **Portée globale** un nom global est un qui est déclaré en dehors de toute classe, la fonction ou l’espace de noms. Cependant, en C++, même ces noms existent avec un espace de noms global implicite. La portée des noms globaux s’étend à partir du point de déclaration jusqu'à la fin du fichier dans lequel ils sont déclarés. Pour les noms globaux, visibilité est également régie par les règles de [liaison](program-and-linkage-cpp.md) qui déterminent si le nom est visible dans d’autres fichiers dans le programme.

- **Étendue de Namespace** un nom qui est déclaré dans un [espace de noms](namespaces-cpp.md), en dehors de toute définition de classe ou un enum ou un bloc de fonction, est visible à partir de son point de déclaration jusqu'à la fin de l’espace de noms. Un espace de noms peut-être être défini dans des blocs multiples entre différents fichiers.

- **Portée locale** un nom déclaré dans une fonction ou une expression lambda, y compris les noms de paramètre, ont une portée locale. Elles sont souvent appelées « variables locales ». Elles ne sont visibles à partir de leur point de déclaration jusqu'à la fin du corps du lambda ou fonction. Portée locale est un type de portée de bloc, qui est abordée plus loin dans cet article.

- **Portée de classe** noms de membres de classe ont une portée de classe, qui étend tout au long de la définition de classe, quel que soit le point de déclaration. Accessibilité des membres de classe est plus contrôlé par le **public**, **privé**, et **protégé** mots clés. Membres publics ou protégés sont accessibles uniquement en utilisant les opérateurs de sélection de membre (**.** ou **->**) ou des opérateurs de pointeur vers membre (**.\***  ou **-> \***).

- **Portée de l’instruction** noms déclarés dans un **pour**, **si**, **tandis que**, ou **basculer** instruction sont visibles jusqu'à la fin de la bloc d’instructions.

- **Portée de la fonction** A [étiquette](labeled-statements.md) a une portée de fonction, ce qui signifie qu’elle est visible dans un corps de fonction même avant son point de déclaration. Portée de fonction rend possible d’écrire des instructions comme `goto cleanup` avant le `cleanup` étiquette est déclarée.

## <a name="hiding-names"></a>Masquage des noms

Vous pouvez masquer un nom en le déclarant dans un bloc englobé. Dans l'illustration suivante, `i` est redéclaré dans le bloc interne, masquant ainsi la variable associée à `i` dans la portée de bloc externe.

 ![Bloc&#45;masquage de nom d’étendue](../cpp/media/vc38sf1.png "vc38SF1") portée de bloc et le masquage de nom

 La sortie du programme représentée dans l'illustration est la suivante :

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> L'argument `szWhat` est considéré comme étant dans la portée de la fonction. Par conséquent, il est traité comme s'il avait été déclaré dans le bloc le plus à l'extérieur de la fonction.

## <a name="hiding-class-names"></a>Masquage des noms de classes

 Vous pouvez masquer les noms de classe en déclarant une fonction, un objet, une variable ou un énumérateur dans la même portée. Toutefois, le nom de classe est toujours accessible lorsque précédé du mot clé **classe**.

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as 
                                       //  class name

    cout << "Opening account with balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with balance of: 15.37
```

> [!NOTE]
> Le nom de classe en tout lieu (`Account`) est appelé, la classe de mot clé doit être utilisée pour le différencier du compte de variable de portée globale. Cette règle ne s’applique pas lorsque le nom de classe apparaît à gauche de l’opérateur de résolution de portée (::). Les noms à gauche de l’opérateur de résolution de portée sont toujours considérés comme des noms de classe.

 L’exemple suivant montre comment déclarer un pointeur vers un objet de type `Account` à l’aide de la **classe** mot clé :

```cpp
class Account *Checking = new class Account( Account );
```

 Le `Account` dans l’initialiseur (entre parenthèses) dans l’instruction précédente a une portée globale ; il s’agit du type **double**.

> [!NOTE]
> La réutilisation des noms d'identificateur, comme l'indique cet exemple, est considérée comme un style de programmation médiocre.

 Pour plus d’informations sur les pointeurs, consultez [Types dérivés](http://msdn.microsoft.com/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Pour plus d’informations sur la déclaration et initialisation des objets de classe, consultez [Classes, Structures et Unions](../cpp/classes-and-structs-cpp.md). Pour plus d’informations sur l’utilisation de la **nouveau** et **supprimer** opérateurs de magasin gratuit, consultez [nouveau et supprimer des opérateurs](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Masquage des noms avec portée globale

 Vous pouvez masquer des noms avec portée globale en déclarant explicitement le même nom dans la portée de bloc. Toutefois, les noms de portée globale est accessible à l’aide de l’opérateur de résolution de portée (`::`).

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>Voir aussi

 [Concepts de base](../cpp/basic-concepts-cpp.md)