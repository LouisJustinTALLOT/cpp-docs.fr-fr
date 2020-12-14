---
description: 'En savoir plus sur : MAPI'
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
ms.openlocfilehash: 634d5d0b2dbbc8a262f624be2b7e294ef6069b96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280805"
---
# <a name="mapi"></a>MAPI

Cet article décrit l’interface de programmation d’applications de messagerie Microsoft (MAPI) pour les développeurs d’applications de message client. MFC fournit la prise en charge d’un sous-ensemble de MAPI dans la classe, `CDocument` mais n’encapsule pas l’intégralité de l’API. Pour plus d’informations, consultez [prise en charge MAPI dans MFC](mapi-support-in-mfc.md).

MAPI est un ensemble de fonctions que les applications à extension messagerie et de messagerie utilisent pour créer, manipuler, transférer et stocker des messages électroniques. Il fournit aux développeurs d’applications les outils nécessaires pour définir l’objectif et le contenu des messages électroniques et leur permet de gérer leurs messages électroniques stockés de manière flexible. MAPI fournit également une interface commune que les développeurs d’applications peuvent utiliser pour créer des applications à extension messagerie et de messagerie indépendantes du système de messagerie sous-jacent.

Les clients de messagerie fournissent une interface utilisateur pour l’interaction avec le système de messagerie Microsoft Windows (WMS). Cette interaction comprend généralement des services de demande de fournisseurs conformes à MAPI, tels que des magasins de messages et des carnets d’adresses.

Pour plus d’informations sur MAPI, consultez les articles sous guide dans la messagerie Win32 (MAPI) du SDK Windows.

## <a name="in-this-section"></a>Dans cette section

[Prise en charge MAPI dans MFC](mapi-support-in-mfc.md)

## <a name="see-also"></a>Voir aussi

[CDocument::OnFileSendMail](reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](reference/coledocument-class.md#onfilesendmail)
