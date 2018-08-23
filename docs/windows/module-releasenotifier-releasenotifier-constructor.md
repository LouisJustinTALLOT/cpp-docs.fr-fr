---
title: Constructeur de module::ReleaseNotifier::ReleaseNotifier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4ab2d5d03516147acda38ea2133d7445695de80
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598786"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier, constructeur

Initialise une nouvelle instance de la **Module::ReleaseNotifier** classe.

## <a name="syntax"></a>Syntaxe

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Paramètres

*release*  
**true** pour supprimer cette instance lorsque la `Release` méthode est appelée ; **false** de ne pas supprimer cette instance.

## <a name="exceptions"></a>Exceptions

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module::ReleaseNotifier, classe](../windows/module-releasenotifier-class.md)