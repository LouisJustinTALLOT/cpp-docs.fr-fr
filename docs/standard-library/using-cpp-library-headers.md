---
description: 'En savoir plus sur : utilisation des en-têtes de bibliothèque C++'
title: Utilisation des en-têtes de bibliothèque C++
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: 7666709f29a7e5bc4119b35ac314ceba15c24930
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153601"
---
# <a name="using-c-library-headers"></a>Utilisation des en-têtes de bibliothèque C++

Vous incluez le contenu d’un en-tête standard en le nommant dans une directive Include.

```cpp
#include <iostream>// include I/O facilities
```

Vous pouvez inclure les en-têtes standard dans n’importe quel ordre, un en-tête standard plusieurs fois ou plusieurs en-têtes standard qui définissent une même macro ou un même type. N’incluez pas un en-tête standard au sein d’une déclaration. Ne définissez pas de macros dotées des mêmes noms que les mots clés avant d’inclure un en-tête standard.

Un en-tête de bibliothèque C++ inclut tous les autres en-têtes de bibliothèque C++ dont il a besoin pour définir les types nécessaires. (Incluez toujours explicitement tous les en-têtes de bibliothèque C++ nécessaires dans une unité de traduction, mais sachez que vous ne savez pas quelles sont les dépendances réelles.) Un en-tête C standard n’intègre jamais un autre en-tête standard. Un en-tête standard déclare ou définit uniquement les entités décrites pour lui dans ce document.

Chaque fonction de la bibliothèque est déclarée dans un en-tête standard. Contrairement au langage C standard, l’en-tête standard ne fournit jamais de macro de masquage du même nom que la fonction qui masque la déclaration de fonction et permet d’obtenir le même effet. Pour plus d’informations sur les macros de masquage, consultez [Conventions de la bibliothèque C++](../standard-library/cpp-library-conventions.md).

Tous les noms autres que **opérateur delete** et **operator new** dans les en-têtes de la bibliothèque C++ sont définis dans l’espace de noms `std` , ou dans un espace de noms imbriqué dans l' `std` espace de noms. Vous faites référence au nom `cin`, par exemple, en tant que `std::cin`. Notez, cependant, que les noms des macros ne sont pas soumis à la qualification d’espace de noms. Par conséquent, vous écrivez toujours `__STD_COMPLEX` sans qualificateur d’espace de noms.

Dans certains environnements de traduction, y compris un en-tête de bibliothèque C++ peut également détourer les noms externes déclarés dans l’espace de noms `std` dans l’espace de noms global, avec des **`using`** déclarations individuelles pour chacun des noms. Sinon, l’en-tête n’introduit *aucun* nom de bibliothèque dans l’espace de noms actuel.

La norme C++ exige que les en-têtes standard C déclarent tous les noms externes dans l’espace de noms `std` , puis les relevages dans l’espace de noms global avec des **`using`** déclarations individuelles pour chacun des noms. Mais, dans certains environnements de traduction, les en-têtes du standard C n’incluent aucune déclaration d’espace de noms, déclarant tous les noms directement dans l’espace de noms global. Par conséquent, la façon la plus portable de traiter les espaces de noms consiste à suivre deux règles :

- Pour déclarer de manière fiable dans l’espace de noms `std` un nom externe qui est traditionnellement déclaré dans \<stdlib.h> , par exemple, incluez l’en-tête \<cstdlib> . Sachez que le nom peut également être déclaré dans l’espace de noms global.

- Pour déclarer de manière fiable dans l’espace de noms global, un nom externe déclaré dans \<stdlib.h> , incluez directement l’en-tête \<stdlib.h> . Sachez que le nom peut également être déclaré dans l’espace de noms `std`.

Par conséquent, si vous souhaitez appeler `std::abort` pour provoquer un arrêt anormal, vous devez inclure \<cstdlib> . Si vous souhaitez appeler `abort` , vous devez inclure \<stdlib.h> .

Vous pouvez également écrire la déclaration :

```cpp
using namespace std;
```

qui rassemble tous les noms de bibliothèque dans l’espace de noms actuel. Si vous écrivez cette déclaration immédiatement après toutes les directives Include, vous haussez les noms dans l’espace de noms global. Vous pouvez ignorer par la suite les considérations d’espace de noms dans le reste de l’unité de traduction. Vous évitez également la plupart des différences entre les différents environnements de traduction.

Sauf indication contraire spécifique, vous ne pouvez pas définir les noms dans l’espace de noms `std` ni dans un espace de noms imbriqué dans l’espace de noms `std`, dans votre programme.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
