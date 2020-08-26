---
title: Classe Platform::ValueType
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: f4ce34fa3f197424833d34bdb866712d412e69c3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846548"
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

### <a name="requirements"></a>Configuration requise

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
