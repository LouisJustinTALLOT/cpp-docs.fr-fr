---
title: Sémantique CString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1638b279f0bd9ee968451ea75ec1c5549e369d9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886152"
---
# <a name="cstring-semantics"></a>Sémantique CString
Même si [CString](../atl-mfc-shared/reference/cstringt-class.md) objets sont des objets dynamiques que peuvent atteindre, ils se comportent comme des types primitifs intégrés et des classes simples. Chaque `CString` objet représente une valeur unique. `CString` objets doivent être considérés comme les chaînes réelles plutôt que comme des pointeurs vers des chaînes.  
  
 Vous pouvez affecter un `CString` objet vers un autre. Toutefois, lorsque vous modifiez l’un des deux `CString` d’objets, l’autre `CString` objet n’est pas modifié, comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 Remarque dans l’exemple que les deux `CString` objets sont considérés comme « égales », car elles représentent la même chaîne de caractères. Le `CString` classe surcharge l’opérateur d’égalité (`==`) pour comparer deux `CString` objets en fonction de leur valeur (contenu) au lieu de leur identité (adresse).  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

