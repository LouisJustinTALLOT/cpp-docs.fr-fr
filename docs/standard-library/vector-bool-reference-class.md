---
description: 'En savoir plus sur : Vector &lt; bool &gt; :: Reference, classe'
title: vector&lt;bool&gt;::reference, classe
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 4e9e4700f8af269f02f038c37d55460bae3a2a96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280480"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference, classe

La `vector<bool>::reference` classe est une classe proxy fournie par la [ \<bool> classe Vector](../standard-library/vector-bool-class.md) à simuler `bool&` .

## <a name="remarks"></a>Notes

Une référence simulée est requise car C++ n'autorise pas en mode natif les références directes aux bits. `vector<bool>` utilise un seul bit par élément, lequel peut être référencé à l'aide de cette classe proxy. Toutefois, la simulation de référence n'est pas terminée car certaines attributions ne sont pas valides. Par exemple, étant donné que l’adresse de l' `vector<bool>::reference` objet ne peut pas être prise, le code suivant qui tente d’utiliser `vector<bool>::operator&` n’est pas correct :

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Inverse la valeur booléenne d'un élément de vecteur.|
|[bool, opérateur](../standard-library/vector-bool-reference-operator-bool.md)|Fournit une conversion implicite de `vector<bool>::reference` en **`bool`** .|
|[opérateur =](../standard-library/vector-bool-reference-operator-assign.md)|Assigne une valeur booléenne à un bit, ou la valeur détenue par un élément référencé à un bit.|

## <a name="requirements"></a>Spécifications

**En-tête**: \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<vector>](../standard-library/vector.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
