---
title: 'TN032 : Mécanisme d’Exception MFC | Documents Microsoft'
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
ms.openlocfilehash: 5256f787534ab408920f7154122ae0c5934019c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380839"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032 : mécanisme d'exception MFC
Les versions précédentes de Visual C++ ne prenait pas en charge le mécanisme d’exception C++ standard, et MFC fournie macros **TRY/CATCH/THROW** qui ont été utilisées à la place. Cette version de Visual C++ prend entièrement en charge les exceptions C++. Cette note couverts certains aspects de l’implémentation avancée des macros précédentes, y compris comment automatiquement les objets de pile en fonction de nettoyage. Exceptions C++ prenant en charge la pile le déroulement par défaut, cette note technique n’est plus nécessaire.  
  
 Reportez-vous à [Exceptions : utilisation des Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) pour plus d’informations sur les différences entre les macros MFC et les nouveaux mots clés C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

