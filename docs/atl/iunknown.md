---
description: 'En savoir plus sur : IUnknown'
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: ddfd35155162275885a1c0c842b4589fa6773a4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152644"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est l’interface de base de chaque autre interface com.  Cette interface définit trois méthodes : [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) permet à un utilisateur d’interface de demander à l’objet un pointeur vers un autre de ses interfaces. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) implémentent le décompte de références sur l’interface.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[IUnknown et héritage d’interface](/windows/win32/com/iunknown-and-interface-inheritance)
