---
description: 'En savoir plus sur : sémantique de CString'
title: Sémantique CString
ms.date: 11/04/2016
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
ms.openlocfilehash: 7c6dde91e7f87908c0c6bc2d49ff455eb79f6eb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167043"
---
# <a name="cstring-semantics"></a>Sémantique CString

Même si les objets [CString](../atl-mfc-shared/reference/cstringt-class.md) sont des objets dynamiques qui peuvent croître, ils agissent comme des types primitifs intégrés et des classes simples. Chaque `CString` objet représente une valeur unique. `CString` les objets doivent être considérés comme des chaînes réelles plutôt que comme des pointeurs vers des chaînes.

Vous pouvez assigner un `CString` objet à un autre. Toutefois, lorsque vous modifiez l’un des deux `CString` objets, l’autre `CString` objet n’est pas modifié, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Notez que dans l’exemple, les deux `CString` objets sont considérés comme « égaux », car ils représentent la même chaîne de caractères. La `CString` classe surcharge l’opérateur d’égalité ( `==` ) pour comparer deux `CString` objets en fonction de leur valeur (contenu) plutôt que de leur identité (adresse).

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
