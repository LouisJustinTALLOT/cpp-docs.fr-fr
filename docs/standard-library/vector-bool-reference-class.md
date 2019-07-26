---
title: vector&lt;bool&gt;::reference, classe
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 65bfc91cf5dc79fb1e5151a6f62c394b4579883b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453216"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference, classe

La classe `vector<bool>::reference` est une classe proxy fournie par la [classe vector\<bool>](../standard-library/vector-bool-class.md) pour simuler `bool&`.

## <a name="remarks"></a>Notes

Une référence simulée est requise car C++ n'autorise pas en mode natif les références directes aux bits. `vector<bool>` utilise un seul bit par élément, lequel peut être référencé à l'aide de cette classe proxy. Toutefois, la simulation de référence n'est pas terminée car certaines attributions ne sont pas valides. Par exemple, étant donné que l’adresse `vector<bool>::reference` de l’objet ne peut pas être prise, le code suivant `vector<bool>::operator&` qui tente d’utiliser n’est pas correct:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Inverse la valeur booléenne d'un élément de vecteur.|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Fournit une conversion implicite `vector<bool>::reference` de en **bool**.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Assigne une valeur booléenne à un bit, ou la valeur détenue par un élément référencé à un bit.|

## <a name="requirements"></a>Configuration requise

**En-tête** : \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<vector>](../standard-library/vector.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
