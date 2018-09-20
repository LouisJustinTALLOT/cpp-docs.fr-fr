---
title: 'TN032 : Mécanisme d’Exception MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.exceptions
dev_langs:
- C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee8ce02af874e1c3c30243a35e8f36acfce63f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414756"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032 : mécanisme d'exception MFC

Les versions précédentes de Visual C++ ne prenaient pas en charge le mécanisme d’exception C++ standard, et MFC fournie macros **TRY/CATCH/THROW** qui ont été utilisés à la place. Cette version de Visual C++ prend entièrement en charge les exceptions C++. Cette note abordé certains des détails d’implémentation avancée des macros précédentes, y compris comment nettoyer automatiquement des objets basée sur la pile. Étant donné que les exceptions C++ prend en charge le déroulement par défaut de la pile, cette note technique n’est plus nécessaire.

Reportez-vous à [Exceptions : utilisation des Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) pour plus d’informations sur les différences entre les macros MFC et les nouveaux mots clés de C++.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

