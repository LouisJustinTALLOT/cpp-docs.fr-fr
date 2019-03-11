---
title: Platform::Metadata::DefaultMemberAttribute (attribut)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
ms.openlocfilehash: 754d41a385e2717989e87c0e06a180f02429d2c2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739097"
---
# <a name="platformmetadatadefaultmemberattribute-attribute"></a>Platform::Metadata::DefaultMemberAttribute (attribut)

Indique la fonction par défaut à appeler parmi plusieurs fonctions surchargées possibles.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class DefaultMember abstract : Attribute
```

## <a name="inheritance"></a>Héritage

[Platform::Object](../cppcx/platform-object-class.md)

[Platform::Metadata::Attribute](../cppcx/platform-metadata-attribute-attribute.md)

### <a name="remarks"></a>Notes

Appliquez l'attribut DefaultMember à une méthode qui est consommée par une application JavaScript.

### <a name="requirements"></a>Spécifications

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Platform::Metadata

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::Metadata (espace de noms)](../cppcx/platform-metadata-namespace.md)
