---
title: Classe de valeur Platform::SizeT | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78d205956f026fe730848afa4c0d6fe7b52b52c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102000"
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

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="ctor"></a>  SizeT::SizeT (constructeur)

Initialise une nouvelle instance de SizeT avec la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Paramètres

*Value1*<br/>
Valeur 32 bits non signée.

*Value2*<br/>
Pointeur vers une valeur 32 bits non signée.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)