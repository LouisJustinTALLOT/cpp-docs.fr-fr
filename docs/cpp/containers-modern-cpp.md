---
title: Conteneurs (Modern C++)
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37b540132fc9ddc03d5eaafd33c545b5db5e7935
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926259"
---
# <a name="containers-modern-c"></a>Conteneurs (Modern C++)

Par défaut, utilisez [Vector](../standard-library/vector-class.md) comme conteneur séquentiel par défaut dans C++. Cela équivaut à `List<T>` dans les langages .net.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilisez [Map](../standard-library/map-class.md) (not `unordered_map`) comme conteneur associatif par défaut. Utilisez [Set](../standard-library/set-class.md), [Multimap](../standard-library/multimap-class.md)et [multijeu](../standard-library/multiset-class.md) pour dégénérer & plusieurs cas.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Lorsque vous avez besoin de l’optimisation des performances, envisagez d’utiliser :

- Le type de [tableau](../standard-library/array-class-stl.md) lorsque l’incorporation est important, par exemple, en tant que membre de classe.

- Conteneurs associatifs non ordonnés, tels que [unordered_map](../standard-library/unordered-map-class.md). Celles-ci ont une surcharge par élément réduite et une recherche à temps constant, mais elles peuvent être plus difficiles à utiliser correctement et efficacement.

- Trié `vector`. Pour plus d’informations, consultez [Algorithmes](../cpp/algorithms-modern-cpp.md).

N’utilisez pas de tableaux de style C. Pour les API plus anciennes qui nécessitent un accès direct aux données, utilisez `f(vec.data(), vec.size());` plutôt des méthodes d’accesseur.

Pour plus d’informations sur les conteneurs, consultez [ C++ conteneurs de bibliothèque standard](../standard-library/stl-containers.md).

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
