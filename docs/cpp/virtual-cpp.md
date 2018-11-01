---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605060"
---
# <a name="virtual-c"></a>virtual (C++)

Le **virtuel** mot clé déclare une fonction virtuelle ou une classe de base virtuelle.

## <a name="syntax"></a>Syntaxe

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Paramètres

*spécificateurs de type*<br/>
Spécifie le type de retour de la fonction membre virtuelle.

*déclarateur de fonction membre*<br/>
Déclare une fonction membre.

*spécificateur d’accès*<br/>
Définit le niveau d’accès à la classe de base, **public**, **protégé** ou **privé**. Peut apparaître avant ou après le **virtuel** mot clé.

*nom de classe de base*<br/>
Identifie un type de classe déclaré précédemment.

## <a name="remarks"></a>Notes

Consultez [fonctions virtuelles](../cpp/virtual-functions.md) pour plus d’informations.

Consultez également les mots clés suivants : [classe](../cpp/class-cpp.md), [privé](../cpp/private-cpp.md), [public](../cpp/public-cpp.md), et [protégé](../cpp/protected-cpp.md).

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)