---
title: Prise en charge d’IDispatch et IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 2dcebd215ff5e1bdf72323323dfbaebd16fa3403
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807414"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Prise en charge d’IDispatch et IErrorInfo

Vous pouvez utiliser la classe de modèle [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pour fournir une implémentation par défaut de la `IDispatch Interface` partie de toutes les interfaces doubles sur votre objet.

Si votre objet utilise le `IErrorInfo` interface pour signaler des erreurs au client, puis votre objet doit prendre en charge la `ISupportErrorInfo Interface` interface. La classe de modèle [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) fournit un moyen simple pour implémenter cela si vous disposez d’une seule interface génère des erreurs sur votre objet.

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)
