---
description: 'En savoir plus sur : classe de valeur Platform :: Sizet'
title: Classe de valeur Platform::SizeT
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: ebcca27a94d23082374daafaa9fd7db180955a30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308014"
---
# <a name="platformsizet-value-class"></a>Classe de valeur Platform::SizeT

Représente la taille d'un objet. SizeT est un type de données non signé.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Membres

|Membre|Description|
|------------|-----------------|
|[SizeT::SizeT, constructeur](#ctor)|Initialise une nouvelle instance de la classe avec la valeur spécifiée.|

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a> Sizet :: Sizet, constructeur

Initialise une nouvelle instance de SizeT avec la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Paramètres

*value1*<br/>
Valeur 32 bits non signée.

*value2*<br/>
Pointeur vers une valeur 32 bits non signée.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
