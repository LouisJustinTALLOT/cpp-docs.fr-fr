---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: ae75bc2e974f374768f1a9e5a0e1ced61e9904b0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023800"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Section spécifique à C++**

Modifie la façon dont le compilateur génère des fonctions wrapper pour les méthodes d'interface double.

## <a name="syntax"></a>Syntaxe

```
no_dual_interfaces
```

## <a name="remarks"></a>Notes

Normalement, le wrapper appelle la méthode via la table de fonctions virtuelles pour l'interface. Avec **no_dual_interfaces**, le wrapper appelle à la place `IDispatch::Invoke` pour appeler la méthode.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)