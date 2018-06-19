---
title: Utilisation des en-têtes de bibliothèque C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30d31f30971184356374b3991fedda474ca27465
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857296"
---
# <a name="using-c-library-headers"></a>Utilisation des en-têtes de bibliothèque C++

Vous incluez le contenu d’un en-tête standard en le nommant dans une directive Include.

```cpp
#include <iostream>// include I/O facilities
```

Vous pouvez inclure les en-têtes standard dans n’importe quel ordre, un en-tête standard plusieurs fois ou plusieurs en-têtes standard qui définissent une même macro ou un même type. N’incluez pas un en-tête standard au sein d’une déclaration. Ne définissez pas de macros dotées des mêmes noms que les mots clés avant d’inclure un en-tête standard.

Un en-tête de bibliothèque C++ inclut tous les autres en-têtes de bibliothèque C++ dont il a besoin pour définir les types nécessaires. (Incluez toutefois toujours explicitement tous les en-têtes de bibliothèque C++ nécessaires dans une unité de traduction, de peur de vous tromper sur ses dépendances réelles.) Un en-tête C standard n’inclut jamais un autre en-tête standard. Un en-tête standard déclare ou définit uniquement les entités décrites pour lui dans ce document.

Chaque fonction de la bibliothèque est déclarée dans un en-tête standard. Contrairement au langage C standard, l’en-tête standard ne fournit jamais de macro de masquage du même nom que la fonction qui masque la déclaration de fonction et permet d’obtenir le même effet. Pour plus d’informations sur les macros de masquage, consultez [Conventions de la bibliothèque C++](../standard-library/cpp-library-conventions.md).

Tous les noms autres que `operator delete` et `operator new` dans les en-têtes de bibliothèque C++ sont définis dans l’espace de noms `std`, ou dans un espace de noms imbriqué dans l’espace de noms `std`. Vous faites référence au nom `cin`, par exemple, en tant que `std::cin`. Notez, cependant, que les noms des macros ne sont pas soumis à la qualification d’espace de noms. Par conséquent, vous écrivez toujours `__STD_COMPLEX` sans qualificateur d’espace de noms.

Dans certains environnements de traduction, l’insertion d’un en-tête de bibliothèque C++ peut hausser les noms externes déclarés dans l’espace de noms `std` vers l’espace de noms global, avec des déclarations `using` individuelles pour chacun de ces noms. Sinon, l’en-tête n’introduit *aucun* nom de bibliothèque dans l’espace de noms actuel.

Le standard C++ nécessite que les en-têtes du standard C déclarent tous les noms externes dans l’espace de noms `std`, puis les haussent vers l’espace de noms global avec des déclarations `using` individuelles pour chacun de ces noms. Mais, dans certains environnements de traduction, les en-têtes du standard C n’incluent aucune déclaration d’espace de noms, déclarant tous les noms directement dans l’espace de noms global. Par conséquent, la façon la plus portable de traiter les espaces de noms consiste à suivre deux règles :

- Pour déclarer sans faute dans l’espace de noms `std` un nom externe traditionnellement déclaré dans \<stdlib.h> par exemple, incluez l’en-tête \<cstdlib>. Sachez que le nom peut également être déclaré dans l’espace de noms global.

- Pour déclarer sans faute dans l’espace de noms global un nom externe déclaré dans \<stdlib.h>, incluez l’en-tête \<stdlib.h> directement. Sachez que le nom peut également être déclaré dans l’espace de noms `std`.

Par conséquent, si vous souhaitez appeler `std::abort` pour déclencher un arrêt anormal, vous devez inclure \<cstdlib>. Si vous souhaitez appeler `abort`, vous devez inclure \<stdlib.h>.

Vous pouvez également écrire la déclaration :

```cpp
using namespace std;
```

qui rassemble tous les noms de bibliothèque dans l’espace de noms actuel. Si vous écrivez cette déclaration immédiatement après toutes les directives Include, vous haussez les noms dans l’espace de noms global. Vous pouvez ignorer par la suite les considérations d’espace de noms dans le reste de l’unité de traduction. Vous évitez également la plupart des différences entre les différents environnements de traduction.

Sauf indication contraire spécifique, vous ne pouvez pas définir les noms dans l’espace de noms `std` ni dans un espace de noms imbriqué dans l’espace de noms `std`, dans votre programme.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
