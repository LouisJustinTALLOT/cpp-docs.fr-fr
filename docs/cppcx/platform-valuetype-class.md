---
description: 'En savoir plus sur : classe Platform :: ValueType'
title: Classe Platform::ValueType
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: e6873b4b884586d06dae6e2fd1966041fd49bcc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307806"
---
# <a name="platformvaluetype-class"></a>Classe Platform::ValueType

Classe de base pour les instances de types de valeur.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Méthodes publiques

| Nom | Description |
|--|--|
| [ValueType :: ToString](#tostring) | Retourne une représentation de l'objet sous forme de chaîne. Héritée de [Platform :: Object](../cppcx/platform-object-class.md). |

### <a name="remarks"></a>Notes

La classe ValueType est utilisée pour construire des types valeur. ValueType est dérivée d’Object, qui a des membres de base. Toutefois, le compilateur détache ces membres de base des types valeur qui sont dérivés de la classe ValueType. Le compilateur réattache ces membres de base lorsqu’un type valeur est boxed.

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="valuetypetostring-method"></a><a name="tostring"></a> ValueType :: ToString, méthode

Retourne une représentation de l'objet sous forme de chaîne.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Valeur de retour

Platform :: String qui représente la valeur.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
