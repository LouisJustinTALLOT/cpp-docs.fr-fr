---
description: 'En savoir plus sur : échange de données'
title: Échange des données
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 9163434d51e3fa248f858434aece8f420e63197d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290442"
---
# <a name="exchanging-data"></a>Échange des données

Comme dans la plupart des boîtes de dialogue, l’échange de données entre la feuille de propriétés et l’application est l’une des fonctions les plus importantes de la feuille de propriétés. Cet article explique comment accomplir cette tâche.

L’échange de données avec une feuille de propriétés est en fait une question d’échange de données avec les pages de propriétés individuelles de la feuille de propriétés. La procédure d’échange de données à l’aide d’une page de propriétés est la même que pour l’échange de données avec une boîte de dialogue, dans la mesure où un objet [CPropertyPage](reference/cpropertypage-class.md) est simplement un objet [CDialog](reference/cdialog-class.md) spécialisé. La procédure tire parti de la fonctionnalité d’échange de données de boîtes de dialogue (DDX) de l’infrastructure, qui échange des données entre des contrôles dans une boîte de dialogue et des variables membres de l’objet de boîte de dialogue.

La différence importante entre l’échange de données avec une feuille de propriétés et une boîte de dialogue normale est que la feuille de propriétés comporte plusieurs pages. vous devez donc échanger des données avec toutes les pages de la feuille de propriétés. Pour plus d’informations sur DDX, consultez [échange et validation de données de boîtes de dialogue](dialog-data-exchange-and-validation.md).

L’exemple suivant illustre l’échange de données entre une vue et deux pages d’une feuille de propriétés :

[!code-cpp[NVC_MFCDocView#4](codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](property-sheets-mfc.md)
