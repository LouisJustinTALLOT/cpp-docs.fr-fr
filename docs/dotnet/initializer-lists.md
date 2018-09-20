---
title: Listes d’initialiseurs | Microsoft Docs
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
ms.openlocfilehash: 981f2737d370dc25ca4e7dc6c20947b3867a0c65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394606"
---
# <a name="initializer-lists"></a>Listes d'initialiseurs

Listes d’initialiseurs de constructeurs sont maintenant appelées avant le constructeur de classe de base.

## <a name="remarks"></a>Notes

Avant Visual C++ 2005, le constructeur de classe de base a été appelé avant la liste d’initialiseurs lors de la compilation avec les Extensions managées pour C++. Désormais, lors de la compilation avec **/CLR**, la liste d’initialiseurs est appelée en premier.

## <a name="see-also"></a>Voir aussi

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)