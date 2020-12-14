---
description: 'En savoir plus sur : TN032 : mécanisme d’exception MFC'
title: "TN032 : mécanisme d'exception MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 847d78762aaf5e04c8a0c1eb2170e951d0b867bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215532"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032 : mécanisme d'exception MFC

Les versions précédentes de Visual C++ ne prenaient pas en charge le mécanisme d’exceptions C++ standard et les macros fournies par MFC **Try/Catch/Throw** utilisaient à la place. Cette version de Visual C++ prend entièrement en charge les exceptions C++. Cette note a abordé certains détails de l’implémentation avancée des macros précédentes, notamment comment nettoyer automatiquement les objets basés sur la pile. Étant donné que les exceptions C++ prennent en charge le déroulement de pile par défaut, cette note technique n’est plus nécessaire.

Reportez-vous aux [exceptions : utilisation de macros MFC et d’exceptions c++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) pour plus d’informations sur les différences entre les macros MFC et les nouveaux mots clés c++.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
