---
title: vector&lt;bool&gt;::reference, classe
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 7930c1cd93cd05a752d4997b9480c766ee26bd99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471498"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference, classe

La classe `vector<bool>::reference` est une classe proxy fournie par la [classe vector\<bool>](../standard-library/vector-bool-class.md) pour simuler `bool&`.

## <a name="remarks"></a>Notes

Une référence simulée est requise car C++ n'autorise pas en mode natif les références directes aux bits. `vector<bool>` utilise un seul bit par élément, lequel peut être référencé à l'aide de cette classe proxy. Toutefois, la simulation de référence n'est pas terminée car certaines attributions ne sont pas valides. Par exemple, étant donné que l’adresse de la `vector<bool>::reference` objet ne peut pas être effectuée, le code suivant qui tente d’utiliser `vector<bool>::operator&` n’est pas correct :

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
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Fournit une conversion implicite de `vector<bool>::reference` à **bool**.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Assigne une valeur booléenne à un bit, ou la valeur détenue par un élément référencé à un bit.|

## <a name="requirements"></a>Configuration requise

**En-tête** : \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<vector>](../standard-library/vector.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
