---
title: Programmes et liaison (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef0f08efbcdf09420d53710a3f16326381f13c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056779"
---
# <a name="program-and-linkage-c"></a>Programme et liaison (C++)

Dans un programme C++, un *symbole*, par exemple un nom de variable ou une fonction peut être déclaré n’importe quel nombre de fois dans son étendue, mais il ne peut être défini qu’une seule fois. Il s’agit de la règle de définition d’un (ODR). Un *déclaration* présente (ou nouveau introduit) un nom dans le programme. Un *définition* introduit un nom et, dans le cas d’une variable, explicitement l’initialise. Un *définition de fonction* constitué la signature et le corps de fonction.

Il s’agit des déclarations :

```cpp
int i;
int f(int x);
```

Il s’agit de définitions :

```cpp
int i{42};
int f(int x){ return x * i; }
```

Un programme se compose d’une ou plusieurs *unités de traduction*. Une unité de traduction se compose d’un fichier d’implémentation (.cpp, .cxx, etc.) et tous les en-têtes (.h, .hpp, etc.) qui contient directement ou indirectement. Chaque unité de traduction est compilée indépendamment par le compilateur, après laquelle l’éditeur de liens fusionne les unités de traduction compilée en un seul *programme*. Les violations de la règle ODR généralement s’affichent comme des erreurs de l’éditeur de liens lorsque le même nom a deux définitions différentes dans les unités de traduction différente.

En règle générale, la meilleure façon de rendre une variable visible dans plusieurs fichiers consiste à placer dans un fichier d’en-tête et ajouter un #include, directive dans chaque fichier .cpp qui nécessite la déclaration. En ajoutant *#include Guard* autour du contenu de l’en-tête, vous assurez-vous que les noms il déclare sont uniquement définies une seule fois.

Toutefois, dans certains cas, il peut être nécessaire de déclarer une variable globale ou une classe dans un fichier .cpp. Dans ce cas, vous devez indiquer au compilateur et l’éditeur de liens si le nom de l’objet s’applique uniquement au un fichier, ou à tous les fichiers.

## <a name="linkage-vs-scope"></a>Liaison et étendue

Le concept de *liaison* fait référence à la visibilité des symboles globaux (par exemple, les variables, les noms de types et les noms de fonction) dans le programme dans sa globalité entre les unités de traduction. Le concept de *étendue* fait référence aux symboles sont déclarés dans un bloc tel qu’un espace de noms, la classe ou le corps de la fonction. Ces symboles sont visibles uniquement dans la portée dans laquelle elles sont définies ; le concept de liaison ne s’applique pas à eux.

## <a name="external-vs-internal-linkage"></a>Externe et une liaison interne

Un *gratuit fonction* est une fonction qui est définie au niveau global ou de la portée de l’espace de noms. Variables globales non-const et fonctions libres par défaut ont *une liaison externe*; ils sont visibles à partir de n’importe quelle unité de traduction dans le programme. Par conséquent, aucun autre objet global (variable, définition de classe, etc.) ne peut avoir ce nom. Un symbole avec *une liaison interne* ou *aucune liaison* est visible uniquement dans l’unité de traduction dans laquelle elle est déclarée. Lorsqu’un nom a une liaison interne, le même nom peut-être exister dans une autre unité de traduction. Les variables déclarées avec les définitions de classe ou le corps de fonction n’ont aucune liaison.

Vous pouvez forcer un nom global pour avoir une liaison interne en déclarant explicitement en tant que **statique**. Cela limite sa visibilité à la même unité de traduction dans laquelle elle est déclarée. Notez que dans ce contexte, **statique** signifie que quelque chose de différent lorsque appliqués aux variables locales.

Les objets suivants ont une liaison interne par défaut :
- objets const
- objets de constexpr
- typedefs
- objets statiques dans la portée espace de noms

Pour donner une liaison externe objet const, déclarez-le en tant que **extern** et lui attribuer une valeur :

```cpp
extern const int value = 42;
```

Consultez [extern](extern-cpp.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)