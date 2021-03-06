---
title: Classes partielles (C++/CX)
description: Comment déclarer et utiliser des classes partielles en C++/CX.
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 70225069c948a50b38ac3642113cf940c86cf8da
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609071"
---
# <a name="partial-classes-ccx"></a>Classes partielles (C++/CX)

Une classe partielle est une construction qui prend en charge les scénarios dans lesquels vous modifiez une partie d'une définition de classe et un logiciel de génération de code automatique, par exemple le concepteur XAML, modifie également le code de la même classe. L'utilisation d'une classe partielle vous permet d'empêcher le concepteur de remplacer votre code. Dans un projet Visual Studio, le **`partial`** modificateur est appliqué automatiquement au fichier généré.

## <a name="syntax"></a>Syntaxe

Pour définir une classe partielle, utilisez le **`partial`** mot clé immédiatement avant la clé-classe de ce qui serait autrement une définition de classe normale. Un mot clé comme **`partial ref class`** est un mot clé contextuel qui contient des espaces blancs. Les définitions partielles sont prises en charge dans les constructions ci-dessous.

- **`class`** ni **`struct`**

- **`ref class`** ni **`ref struct`**

- **`value class`** ni **`value struct`**

- **`enum`** ni **`enum class`**

- **`ref interface`**, **`interface class`** , **`interface struct`** ou **`__interface`**

- **`union`**

Cet exemple illustre une partie **`ref class`** :

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Contents

Une définition de classe partielle peut contenir tout ce que la définition de classe complète peut contenir si le **`partial`** mot clé a été omis. Sauf une exception, cela inclut toutes les constructions valides, telles que les classes de base, les données membres, les fonctions de membre, les énumérations, les déclarations Friend et les attributs. Les définitions inline des données membres statiques sont autorisées.

L'unique exception est l'accessibilité de la classe. Par exemple, l'instruction `public partial class MyInvalidClass {/* ... */};` est une erreur. Aucun spécificateur d'accès utilisé dans une définition de classe partielle pour MyInvalidClass n'affecte l'accessibilité par défaut dans une définition de classe partielle ou complète suivante pour MyInvalidClass.

Le fragment de code suivant illustre cette accessibilité. Dans la première classe partielle, `Method1` est publique car son accessibilité est publique. Dans la deuxième classe partielle, `Method2` est privée car l'accessibilité de la classe est par défaut privée.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Déclaration

Une définition partielle d’une classe telle que `MyClass` n’est qu’une déclaration de MyClass. Autrement dit, il introduit uniquement le nom `MyClass` . `MyClass` ne peut pas être utilisé d’une manière qui requiert une définition de classe, par exemple, en connaissant la taille de `MyClass` ou à l’aide d’une base ou d’un membre de `MyClass` . `MyClass` est considéré comme étant défini uniquement lorsque le compilateur rencontre une définition non partielle de `MyClass` .

L'exemple ci-dessous illustre le comportement de déclaration d'une classe partielle. Après la #1 de déclaration, `MyClass` peut être utilisé comme s’il avait été écrit en tant que déclaration anticipée `ref class MyClass;` . La déclaration n°2 équivaut à la déclaration n°1. La déclaration n°3 est valide car il s'agit d'une déclaration anticipée d'une classe. Mais la déclaration n°4 n'est pas valide car

`MyClass`n'est pas entièrement défini.

La déclaration #5 n’utilise pas le **`partial`** mot clé, et la déclaration est entièrement définie `MyClass` . Par conséquent, la déclaration #6 est valide.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Nombre et classement

Il peut y avoir zéro définition de classe partielle ou plus pour chaque définition de classe complète.

Chaque définition de classe partielle d’une classe doit précéder lexicalement la seule définition complète de cette classe, mais ne doit pas précéder les déclarations anticipées de la classe. S'il n'existe aucune définition complète de la classe, les déclarations de classe partielles ne peuvent être que des déclarations anticipées.

Toutes les clés de classe telles que **`class`** et **`struct`** doivent correspondre. Par exemple, c’est une erreur de coder `partial class X {}; struct X {};`.

L'exemple suivant illustre le nombre et le classement. La dernière déclaration partielle échoue car la classe est déjà définie.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Définition complète

Dans la phase de définition complète de la classe X, le comportement est identique comme si la définition de X a déclaré toutes les classes de base, les membres, etc., dans l'ordre dans lequel ils ont été rencontrés et définis dans les classes partielles. En d'autres termes, le contenu des classes partielles est traité comme s'il a été écrit dans la phase de définition complète de la classe, et la recherche de nom et d'autres règles de langage sont appliquées dans la phase de définition complète de la classe comme si le contenu des classes partielles a été écrit à ce moment

Les deux exemples de code ci-dessous ont une signification et un effet identiques. Le premier exemple utilise une classe partielle et le deuxième exemple ne le fait pas.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Modèles

Une classe partielle ne peut pas être un modèle.

## <a name="restrictions"></a>Restrictions

Une classe partielle ne peut pas s'étendre au-delà d'une unité de traduction.

Le **`partial`** mot clé est pris en charge uniquement en association avec le mot **`ref class`** clé ou le **`value class`** mot clé.

### <a name="examples"></a>Exemples

L'exemple suivant définit la classe `Address` pour deux fichiers de code. Le concepteur modifie `Address.details.h` et vous modifiez `Address.h`. Seule la définition de classe dans le premier fichier utilise le **`partial`** mot clé.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Voir aussi

[Système de types](../cppcx/type-system-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
