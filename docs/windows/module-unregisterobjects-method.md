---
title: Module::unregisterobjects, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87fb8ece3e1897a3ba460403d273bd649784ad44
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400424"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects, méthode

Annule l’inscription d’objets dans le module spécifié afin que les autres applications ne peuvent pas s’y connecter.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Pointeur vers un module.

*Nom du serveur*<br/>
Nom de qualification qui spécifie un sous-ensemble d’objets affectés par cette opération.

## <a name="return-value"></a>Valeur de retour

S_OK si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)