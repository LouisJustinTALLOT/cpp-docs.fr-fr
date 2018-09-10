---
title: Utilisation du contrôle RichEdit 1.0 avec MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27e3ad32500d1b0ff0efa2dab40888f163744bb1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318705"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Utilisation du contrôle RichEdit 1.0 avec MFC

Pour utiliser un contrôle RichEdit, vous devez d’abord appeler [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) pour charger le contrôle RichEdit 2.0 (RICHED20. DLL), ou appelez [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) pour charger l’ancien contrôle RichEdit 1.0 (Riched32). (DLL).

Vous pouvez utiliser actuel [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) classe avec l’ancien contrôle RichEdit 1.0, mais `CRichEditCtrl` est conçu uniquement pour prendre en charge le contrôle RichEdit 2.0. Étant donné que RichEdit 1.0 et RichEdit 2.0 sont très similaires, la plupart des méthodes fonctionneront ; Notez, toutefois, il existe des différences entre les contrôles 1.0 et 2.0, et certaines méthodes peuvent fonctionner de manière incorrecte ou ne fonctionne pas du tout.

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Dépannage de l’Éditeur de boîtes de dialogue](../windows/troubleshooting-the-dialog-editor.md)  
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)