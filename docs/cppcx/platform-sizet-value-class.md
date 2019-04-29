---
title: Classe de valeur Platform::SizeT
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 7f81cb9e1fc2ef7a74cb3878c369e4d7d14e3d90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330133"
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

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="ctor"></a>  SizeT::SizeT (constructeur)

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

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
