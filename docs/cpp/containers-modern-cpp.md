---
title: Conteneurs (Modern C++) | Documents Microsoft
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49a77234b679fd61d801bb78d751891467d6b4e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412073"
---
# <a name="containers-modern-c"></a>Conteneurs (Modern C++)

Par défaut, utilisez [vecteur](../standard-library/vector-class.md) en tant que le conteneur par défaut séquentiel en C++. Cela est équivalent à `List<T>` dans les langages .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilisez [carte](../standard-library/map-class.md) (pas `unordered_map`) comme conteneur associatif par défaut. Utilisez [définir](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), et [multiset](../standard-library/multiset-class.md) dégénérée & plusieurs cas.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Lors de l’optimisation des performances est nécessaire, envisagez d’utiliser :

- Le [tableau](../standard-library/array-class-stl.md) lorsque l’incorporation est importante, par exemple, en tant qu’un membre de classe de type.

- Désordonnés tels que les conteneurs associatifs [unordered_map](../standard-library/unordered-map-class.md). Ces messages ont surcharge élément inférieur et une recherche constante, mais ils peuvent être plus difficile à utiliser correctement et efficacement.

- Triées **vecteur**. Pour plus d’informations, consultez [Algorithmes](../cpp/algorithms-modern-cpp.md).

N’utilisez pas les tableaux de style C. Pour plus anciennes API qui doivent pouvoir accéder aux données directement, utilisez les méthodes d’accesseur telles que `f(vec.data(), vec.size());` à la place.

Pour plus d’informations sur les conteneurs, consultez [conteneurs de bibliothèque C++ Standard](../standard-library/stl-containers.md).

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)  
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)  
