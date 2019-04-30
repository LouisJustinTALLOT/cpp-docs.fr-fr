---
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
ms.openlocfilehash: 59f463d103e233a1d9b25da3243a16f67263c815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392295"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Constructeurs de copie et opérateurs d'assignation de copie (C++)

> [!NOTE]
> À compter de C ++ 11, deux types d’assignations sont prises en charge : *copier devoir* et *assignation de déplacement*. Dans cet article « assignation » signifie assignation de copie, sauf spécification contraire. Pour plus d’informations sur l’assignation de déplacement, consultez [constructeurs de déplacement et opérateurs d’assignation déplacer (C++)](move-constructors-and-move-assignment-operators-cpp.md).
>
> Les opérations d'assignation et d'initialisation génèrent une copie des objets.

- **Affectation**: Lorsque la valeur d’un objet est affectée à un autre objet, le premier objet est copié vers le deuxième objet. Par conséquent,

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   entraîne la copie de la valeur de `b` dans `a`.

- **L’initialisation**: L’initialisation se produit lorsqu’un nouvel objet est déclaré, lorsque les arguments sont passés aux fonctions par valeur, ou lorsque les valeurs sont retournées à partir de fonctions par valeur.

Vous pouvez définir la sémantique de « copie » pour les objets de type classe. Par exemple, prenons le code suivant :

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Ce code pourrait signifier « copier le contenu de FILE1.DAT vers FILE2.DAT » ou « ignorer FILE2.DAT et faire de `b` un deuxième handle vers FILE1.DAT ». Vous devez lier à chaque classe la sémantique de copie appropriée, comme suit.

- À l’aide de l’opérateur d’assignation **opérateur =** avec une référence au type de classe en tant que le type de retour et le paramètre est passé par **const** référence — par exemple `ClassName& operator=(const ClassName& x);`.

- En utilisant le constructeur de copie.

Si vous ne déclarez pas de constructeur de copie, le compilateur génère un constructeur de copie de membre à membre à votre place.  Si vous ne déclarez pas d'opérateur d'assignation de copie, le compilateur génère un opérateur d'assignation de copie de membre à membre à votre place. La déclaration d'un constructeur de copie n'entraîne pas la suppression de l'opérateur d'assignation de copie généré par le compilateur, et vice versa. Si vous implémentez l'un des deux, nous vous recommandons d'implémenter également l'autre afin que la signification du code soit claire.

Le constructeur de copie accepte un argument de type <em>nom de la classe</em><strong>&</strong>, où *nom de la classe* est le nom de la classe pour laquelle le constructeur est défini. Exemple :

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
> Vérifiez le type d’argument du constructeur de copie **const** <em>nom de la classe</em> <strong>&</strong> autant que possible. Cela empêche le constructeur de copie de modifier accidentellement l'objet à partir duquel il effectue la copie. Il permet également de copie à partir de **const** objets.

## <a name="compiler-generated-copy-constructors"></a>Constructeurs de copie générés par le compilateur

Les constructeurs de copie généré par le compilateur, telles que les constructeurs de copie défini par l’utilisateur, ont un seul argument de type « référence à *nom de la classe*. » Une exception est lorsque toutes les classes de base et les classes de membre possèdent des constructeurs de copie déclarés comme prenant un argument unique de type **const** <em>nom de la classe</em><strong>&</strong>. Dans ce cas, les arguments du constructeur de copie généré par le compilateur est également **const**.

Lorsque le type d’argument au constructeur de copie n’est pas **const**, l’initialisation en copiant un **const** objet génère une erreur. L’inverse n’est pas vrai : Si l’argument est **const**, vous pouvez initialiser en copiant un objet qui n’est pas **const**.

Opérateurs d’assignation généré par le compilateur suivent le même modèle aux **const.** Ils acceptent un argument unique de type <em>nom de la classe</em> <strong>&</strong> à moins que les opérateurs d’assignation dans toutes les classes de base et membres acceptent des arguments de type **const** <em>nom de la classe</em><strong>&</strong>. Dans ce cas, la classe générée du affectation opérateur prend un **const** argument.

> [!NOTE]
> Lorsque des classes de base virtuelles sont initialisées par des constructeurs de copie, générés par le compilateur ou définis par l'utilisateur, elles ne sont initialisées qu'une seule fois : au moment où elles sont construites.

Les conséquences sont semblables à celles du constructeur de copie. Lorsque le type d’argument n’est pas **const**, affectation à partir d’un **const** objet génère une erreur. L’inverse n’est pas vrai : Si un **const** valeur est assignée à une valeur qui n’est pas **const**, l’assignation réussit.

Pour plus d’informations sur les opérateurs d’assignation surchargés, consultez [attribution](../cpp/assignment.md).