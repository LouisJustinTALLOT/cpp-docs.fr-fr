---
title: 'TN032 : Mécanisme d’Exception MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 210e47e117cd602ba77edd330205385f54199ce5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305656"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032 : Mécanisme d’Exception MFC

Les versions précédentes de Visual C++ ne prenaient pas en charge le mécanisme d’exception C++ standard, et MFC fournie macros **TRY/CATCH/THROW** qui ont été utilisés à la place. Cette version de Visual C++ prend entièrement en charge les exceptions C++. Cette note abordé certains des détails d’implémentation avancée des macros précédentes, y compris comment nettoyer automatiquement des objets basée sur la pile. Étant donné que les exceptions C++ prend en charge le déroulement par défaut de la pile, cette note technique n’est plus nécessaire.

Reportez-vous à [Exceptions : À l’aide de Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) pour plus d’informations sur les différences entre les macros MFC et les nouveaux mots clés de C++.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
