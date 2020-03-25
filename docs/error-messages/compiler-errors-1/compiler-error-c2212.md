---
title: Erreur du compilateur C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: bf478c96e76a4fe139caee79f497a0abe7f70824
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206676"
---
# <a name="compiler-error-c2212"></a>Erreur du compilateur C2212

'identificateur' : __based pas disponible pour les pointeurs vers des fonctions

Les pointeurs vers des fonctions ne peuvent pas être déclarés `__based`. Si vous avez besoin de données basées sur du code, utilisez le mot clé `__declspec` ou le pragma `data_seg`.
