---
title: '&lt;vector&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: 29b23ec4afe32d1aa383afd4fdaf3ca280d49161
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955258"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt;, fonctions


## <a name="swap"></a>  swap

Échange les éléments de deux vecteurs.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*right*  
 Le vecteur qui fournit les éléments à échanger, ou le vecteur dont les éléments doivent être échangés avec ceux du vecteur *gauche*.

*left*  
 Le vecteur dont les éléments doivent être échangés avec ceux du vecteur *droit*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur vector pour exécuter la fonction membre `left`. [Vector::swap](../standard-library/vector-class.md) *(droit*). Il s’agit d’instances de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template** \< **class T**> **void swap**( **T&**, **T&**), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [vector::swap](../standard-library/vector-class.md).

## <a name="see-also"></a>Voir aussi

[\<vector>](../standard-library/vector.md)<br/>
