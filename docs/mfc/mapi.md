---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279105"
---
# <a name="mapi"></a>MAPI

Cet article décrit le Microsoft MAPI Messaging Application Programming Interface () pour les développeurs d’applications client message. MFC fournit la prise en charge pour un sous-ensemble de MAPI dans la classe `CDocument` mais n’encapsule ne pas l’ensemble de l’API. Pour plus d’informations, consultez [prise en charge MAPI dans MFC](../mfc/mapi-support-in-mfc.md).

MAPI est un ensemble de fonctions que les applications de messagerie et de messagerie prenant en charge utilisent pour créer, manipuler, transférer et stocker des messages électroniques. Il offre aux développeurs d’applications les outils pour définir l’objectif et le contenu des messages électroniques et la flexibilité à la gestion des messages électroniques stockés. MAPI fournit également une interface commune que les développeurs d’applications peuvent utiliser pour créer la messagerie et les applications prenant en charge la messagerie indépendantes du système de messagerie sous-jacent.

Les clients de messagerie fournissent une interface humaine pour l’interaction avec Microsoft Windows Messaging System (WMS). Cette interaction comprend les demandes de services à partir des fournisseurs compatible MAPI tels que les banques de messages et les carnets d’adresses.

Pour plus d’informations sur MAPI, consultez les articles sous Guide dans Win32 MAPI (Messaging) du Kit de développement Windows.

## <a name="in-this-section"></a>Dans cette section

[Prise en charge MAPI dans les MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Voir aussi

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
