---
title: Erreur des LNK2023 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090319"
---
# <a name="linker-tools-error-lnk2023"></a>Erreur des outils Éditeur de liens LNK2023

dll incorrecte ou point d’entrée \<dll ou point d’entrée >

L’éditeur de liens charge une version incorrecte de msobj90.dll. Vérifiez que link.exe et msobj90.dll dans votre chemin d’accès ont la même version.

Une dépendance de msobj90.dll ne peut pas être présente. La liste des dépendances de msobj90.dll est :

- Msvcr90.dll

- Kernel32.dll

Vérifiez votre ordinateur pour toutes les autres copies de msobj90.dll pouvant être obsolètes.