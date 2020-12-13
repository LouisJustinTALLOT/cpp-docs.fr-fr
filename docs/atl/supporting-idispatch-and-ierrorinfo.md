---
description: 'En savoir plus sur les éléments suivants : prise en charge de IDispatch et IErrorInfo'
title: Prise en charge d’IDispatch et d’IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 4622c8811fafc9512400345e5876dd24c466bc93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138448"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Prise en charge d’IDispatch et d’IErrorInfo

Vous pouvez utiliser la classe de modèle [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pour fournir une implémentation par défaut de la `IDispatch Interface` partie des interfaces doubles sur votre objet.

Si votre objet utilise l' `IErrorInfo` interface pour signaler les erreurs au client, votre objet doit prendre en charge l' `ISupportErrorInfo Interface` interface. La classe de modèle [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) offre un moyen simple d’implémenter cela si vous n’avez qu’une seule interface qui génère des erreurs sur votre objet.

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)
