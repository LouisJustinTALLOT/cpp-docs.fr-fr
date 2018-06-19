---
title: vector&lt;bool&gt;::reference::operator bool | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0fd249dd7591caaaf62a0b8a698085efedb1f25
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854533"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Fournit une conversion implicite de `vector<bool>::reference` en `bool`.

## <a name="syntax"></a>Syntaxe

```cpp
operator bool() const;
```

## <a name="return-value"></a>Valeur de retour

La valeur booléenne de l’élément de l’objet [vector\<bool>](../standard-library/vector-bool-class.md).

## <a name="remarks"></a>Notes

L'objet `vector<bool>` ne peut pas être modifié par cet opérateur.

## <a name="requirements"></a>Spécifications

**En-tête :** \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[vecteur\<bool > :: classe de référence](../standard-library/vector-bool-reference-class.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
