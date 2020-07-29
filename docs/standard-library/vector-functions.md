---
title: '&lt;vector&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: bf28e44b4f603b1e4d6a87f0c28b42d6cc159980
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224550"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt;, fonctions

## <a name="swap"></a><a name="swap"></a>échange

Échange les éléments de deux vecteurs.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Vecteur qui fournit les éléments à permuter, ou vecteur dont les éléments doivent être échangés avec ceux du vecteur *restant*.

*gauche*\
Vecteur dont les éléments doivent être échangés avec ceux du vecteur de *droite*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur le vecteur de la classe de conteneur pour exécuter la fonction membre `left` . [vector :: swap](../standard-library/vector-class.md) *(Right*). Il s’agit d’instances de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **`template`** \< **class T**> **void swap**( **t&**, **t&**), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [vector::swap](../standard-library/vector-class.md).
