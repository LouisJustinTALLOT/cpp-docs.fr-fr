---
description: 'En savoir plus sur : constructeurs de copie et opérateurs d’assignation de copie (C++)'
title: Constructeurs de copie et opérateurs d'assignation de copie (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: 881470c92e0261dc5c4cd63876d7cb59fcc68fef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344573"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Constructeurs de copie et opérateurs d'assignation de copie (C++)

> [!NOTE]
> À partir de C++ 11, deux types d’attributions sont pris en charge dans le langage : *assignation de copie* et *assignation de déplacement*. Dans cet article « assignation » signifie assignation de copie, sauf spécification contraire. Pour plus d’informations sur l’assignation de déplacement, consultez [constructeurs de déplacement et opérateurs d’assignation de déplacement (C++)](move-constructors-and-move-assignment-operators-cpp.md).
>
> Les opérations d'assignation et d'initialisation génèrent une copie des objets.

- **Assignation**: quand la valeur d’un objet est assignée à un autre objet, le premier objet est copié dans le deuxième objet. Par conséquent,

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   entraîne la copie de la valeur de `b` dans `a`.

- **Initialisation**: l’initialisation se produit lorsqu’un nouvel objet est déclaré, lorsque des arguments sont passés à des fonctions par valeur, ou lorsque des valeurs sont retournées à partir de fonctions par valeur.

Vous pouvez définir la sémantique de « copie » pour les objets de type classe. Considérez par exemple le code suivant :

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Ce code pourrait signifier « copier le contenu de FILE1.DAT vers FILE2.DAT » ou « ignorer FILE2.DAT et faire de `b` un deuxième handle vers FILE1.DAT ». Vous devez lier à chaque classe la sémantique de copie appropriée, comme suit.

- En utilisant l’opérateur d’assignation **Operator =** avec une référence au type de classe comme type de retour et le paramètre passé par **`const`** référence, par exemple `ClassName& operator=(const ClassName& x);` .

- En utilisant le constructeur de copie.

Si vous ne déclarez pas de constructeur de copie, le compilateur génère un constructeur de copie de membre à membre à votre place.  Si vous ne déclarez pas d'opérateur d'assignation de copie, le compilateur génère un opérateur d'assignation de copie de membre à membre à votre place. La déclaration d'un constructeur de copie n'entraîne pas la suppression de l'opérateur d'assignation de copie généré par le compilateur, et vice versa. Si vous implémentez l'un des deux, nous vous recommandons d'implémenter également l'autre afin que la signification du code soit claire.

Le constructeur de copie accepte un argument de type <em>Class-Name</em> <strong>&</strong> , où *Class-Name* est le nom de la classe pour laquelle le constructeur est défini. Par exemple :

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> Définissez le type de la classe d’argument du constructeur de copie **`const`** <em></em> <strong>&</strong> chaque fois que possible. Cela empêche le constructeur de copie de modifier accidentellement l'objet à partir duquel il effectue la copie. Il permet également la copie à partir d' **`const`** objets.

## <a name="compiler-generated-copy-constructors"></a>Constructeurs de copie générés par le compilateur

Les constructeurs de copie générés par le compilateur, comme les constructeurs de copie définis par l’utilisateur, ont un seul argument de type « référence à *Class-Name*». Une exception est quand toutes les classes de base et les classes de membre ont des constructeurs de copie déclarés comme acceptant un argument unique de type **`const`** <em>Class-Name</em> <strong>&</strong> . Dans ce cas, l’argument du constructeur de copie généré par le compilateur est également **`const`** .

Lorsque le type d’argument du constructeur de copie n’est pas **`const`** , l’initialisation par copie d’un **`const`** objet génère une erreur. L’inverse n’est pas vrai : si l’argument est **`const`** , vous pouvez initialiser en copiant un objet qui n’est pas **`const`** .

Les opérateurs d’assignation générés par le compilateur suivent le même modèle en ce qui concerne **const.** Ils acceptent un argument unique de type <em>Class-Name</em> <strong>&</strong> , sauf si les opérateurs d’assignation dans toutes les classes de base et les classes de membre acceptent des arguments de type **`const`** <em>Class-Name</em> <strong>&</strong> . Dans ce cas, l’opérateur d’assignation généré de la classe prend un **`const`** argument.

> [!NOTE]
> Lorsque des classes de base virtuelles sont initialisées par des constructeurs de copie, générés par le compilateur ou définis par l'utilisateur, elles ne sont initialisées qu'une seule fois : au moment où elles sont construites.

Les conséquences sont semblables à celles du constructeur de copie. Lorsque le type d’argument n’est pas **`const`** , l’assignation d’un **`const`** objet génère une erreur. L’inverse n’est pas vrai : si une **`const`** valeur est assignée à une valeur qui n’est pas **`const`** , l’assignation est réussie.

Pour plus d’informations sur les opérateurs d’assignation surchargés, consultez [affectation](../cpp/assignment.md).
