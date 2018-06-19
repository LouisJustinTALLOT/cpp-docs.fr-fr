---
title: Listes d’initialiseurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6634b749480e5108548de0c8b53f8b09cc5a42c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127950"
---
# <a name="initializer-lists"></a>Listes d'initialiseurs
Listes d’initialiseurs de constructeurs sont maintenant appelées avant le constructeur de classe de base.  
  
## <a name="remarks"></a>Notes  
 Avant Visual C++ 2005, le constructeur de classe de base a été appelé avant la liste d’initialiseurs lors de la compilation avec les Extensions managées pour C++. Désormais, lors de la compilation avec **/CLR**, la liste d’initialiseurs est appelée en premier.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)