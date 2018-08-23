---
title: Ftmbase::createglobalinterfacetable, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs:
- C++
helpviewer_keywords:
- CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c042b6bd17da3459f499f9eb1c9167343c2e2ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578771"
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable, méthode

Crée un tableau global d’interface (GIT).

## <a name="syntax"></a>Syntaxe

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Paramètres

*GIT*  
Lorsque cette opération se termine, un pointeur vers un tableau global d’interface.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez le `IGlobalInterfaceTable` rubrique dans le **Interfaces COM** sous-rubrique de la **référence COM** rubrique dans MSDN Library.

## <a name="requirements"></a>Configuration requise

**En-tête :** ftm.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[FtmBase, classe](../windows/ftmbase-class.md)