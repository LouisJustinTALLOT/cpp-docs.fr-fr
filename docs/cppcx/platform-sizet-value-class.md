---
title: Classe de valeur Platform::SizeT
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 02fe62165ce40d267f156eaeb3ad93f636c9ab73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604215"
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