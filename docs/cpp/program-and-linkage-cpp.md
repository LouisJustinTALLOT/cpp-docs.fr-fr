---
title: Programme et liaison (C++) | Documents Microsoft
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
ms.openlocfilehash: 4154f0951b46b1c8badc0224845d2881cc8ad573
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421365"
---
# <a name="program-and-linkage--c"></a>Programme et liaison (C++)

Dans un programme C++, chaque symbole global peut être défini qu’une seule fois, même si le programme se compose de plusieurs unités de traduction. Une unité de traduction se compose d’un fichier d’implémentation (.cpp, .hpp, .cxx, etc.) et tous les en-têtes qui contient directement ou indirectement. Un programme se compose d'un ou de plusieurs unités de traduction liées ensemble. 

## <a name="linkage-vs-scope"></a>Liaison et étendue

Le concept de *une liaison* fait référence à la visibilité des symboles globaux (par exemple, les variables, les noms de types et les noms de fonctions) au sein du programme dans son ensemble entre les unités de traduction. Le concept de *étendue* fait référence à des symboles qui sont déclarées dans un bloc tel qu’un espace de noms, la classe ou le corps de la fonction. Ces symboles sont visibles uniquement dans l’étendue dans laquelle elles sont définies ; le concept de liaison ne s’applique pas à ceux-ci.

## <a name="external-vs-internal-linkage"></a>Externe et une liaison interne

Les variables globales non-const et fonctions libres par défaut ont une liaison externe ; ils sont visibles à partir de n’importe quelle unité de traduction dans le programme. Vous pouvez substituer ce comportement en explicitement les déclarer en tant que **statique** qui limite leur visibilité à la même unité de traduction dans lequel ils sont déclarés. Cette signification de **statique** est différente de celle de sa signification lorsqu’ils sont appliqués aux variables locales. Les variables déclarées en tant que **const** ont une liaison interne par défaut.

## <a name="extern-constexpr-linkage"></a>Liaison de constexpr externe

Dans les versions antérieures de Visual Studio, le compilateur a toujours une liaison interne de variable constexpr même quand la variable a été marqué comme extern. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur (/Zc:externConstexpr) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient un constexpr variable extern déclarée, elle doit être marquée comme **__declspec (selectany)** afin d’avoir correctement de ses déclarations en double combinées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>Voir aussi

 [Concepts de base](../cpp/basic-concepts-cpp.md)