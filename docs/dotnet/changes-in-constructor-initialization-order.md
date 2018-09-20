---
title: Modifications dans l’ordre d’initialisation des constructeurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397687"
---
# <a name="changes-in-constructor-initialization-order"></a>Modifications dans l'ordre d'initialisation des constructeurs

L’ordre d’initialisation pour les constructeurs de classe a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

## <a name="comparison-of-constructor-initialization-order"></a>Comparaison de l’ordre d’initialisation des constructeurs

Sous les Extensions managées pour C++, l’initialisation du constructeur s’est produite dans l’ordre suivant :

1. Le constructeur de la classe de base, le cas échéant, est appelé.

1. La liste d’initialisation de la classe est évaluée.

1. Le corps de code du constructeur de classe est exécuté.

Cet ordre d’exécution suit les mêmes conventions que dans la programmation en C++ native. Le nouveau langage Visual C++ prescrit l’ordre d’exécution suivants pour les classes CLR :

1. La liste d’initialisation de la classe est évaluée.

1. Le constructeur de la classe de base, le cas échéant, est appelé.

1. Le corps de code du constructeur de classe est exécuté.

Notez que cette modification s’applique uniquement aux classes CLR ; les classes natives dans Visual C++ a toujours suivent les conventions antérieures. Dans les deux cas, ces règles en cascade vers le haut dans la chaîne de l’ensemble de la hiérarchie d’une classe donnée.

Prenons l’exemple de code suivant à l’aide des Extensions managées pour C++ :

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Suivant l’ordre de l’initialisation du constructeur prescrit ci-dessus, nous devrions voir l’ordre suivant d’exécution lorsque de nouvelles instances de classe `B` sont construits :

1. Le constructeur de la classe de base `A` est appelé. Le `_n` membre est initialisé à `1`.

1. La liste d’initialisation pour la classe `B` est évaluée. Le `_m` membre est initialisé à `1`.

1. Le corps de code de classe `B` est exécutée.

Examinons à présent le même code dans la nouvelle syntaxe Visual C++ :

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

L’ordre d’exécution lorsque de nouvelles instances de classe `B` sont construites sous la nouvelle syntaxe est :

1. La liste d’initialisation pour la classe `B` est évaluée. Le `_m` membre est initialisé à `0` (`0` est la valeur non initialisée de la `_m` membre de classe).

1. Le constructeur de la classe de base `A` est appelé. Le `_n` membre est initialisé à `1`.

1. Le corps de code de classe `B` est exécutée.

Notez qu’une syntaxe similaire produit des résultats différents pour ces exemples de code. Le constructeur de classe `B` dépend d’une valeur à partir de la classe de base `A` pour initialiser son membre. Toutefois, le constructeur de classe `A` n’a pas encore été appelé. Une telle dépendance peut être particulièrement dangereuse lorsque la classe héritée dépend d’une allocation de mémoire ou une ressource peut se produire dans le constructeur de classe de base.

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Ce que signifie le passage d’Extensions managées pour C++ vers Visual C++ 2010

Dans de nombreux cas, les modifications apportées à l’ordre d’exécution des constructeurs de classe doivent être transparentes pour le programmeur, car les classes de base n’ont aucune notion du comportement des classes héritées. Toutefois, comme l’illustrent ces exemples de code, les constructeurs des classes héritées peuvent être considérablement affectées lorsque leurs listes d’initialisation dépendent des valeurs des membres de classe de base. Lorsque vous déplacez votre code à partir des Extensions managées pour C++ vers la nouvelle syntaxe, envisagez de déplacer ces constructions dans le corps du constructeur de classe, où l’exécution est garantie dernière.

## <a name="see-also"></a>Voir aussi

[Types managés (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Constructeurs](../cpp/constructors-cpp.md)
