---
title: Platform::Metadata::DefaultMemberAttribute (attribut)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
ms.openlocfilehash: a4b3d5e8ab5d6ce254560bc84daceac74e2c9ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486656"
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

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform::Metadata

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::Metadata (espace de noms)](../cppcx/platform-metadata-namespace.md)