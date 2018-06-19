---
title: Sémantique de CString | Documents Microsoft
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
ms.openlocfilehash: b1765f1f7f4103b1b2cfe6012b42ebef12f8863f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356577"
---
# <a name="cstring-semantics"></a>Sémantique CString
Bien que [CString](../atl-mfc-shared/reference/cstringt-class.md) les objets sont des objets dynamiques peuvent atteindre, ils se comportent comme des types primitifs intégrés et des classes simples. Chaque `CString` objet représente une valeur unique. `CString` objets doivent être considérés comme les chaînes réelles plutôt que comme des pointeurs vers des chaînes.  
  
 Vous pouvez affecter un **CString** objet vers un autre. Toutefois, lorsque vous modifiez l’un des deux `CString` des objets, l’autre `CString` objet n’est pas modifié, comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 Remarque dans l’exemple que les deux `CString` objets sont considérés comme « égales à », car elles représentent la même chaîne de caractères. Le `CString` classe surcharge l’opérateur d’égalité (`==`) pour comparer deux `CString` objets en fonction de leur valeur (contenu) au lieu de leur identité (adresse).  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

