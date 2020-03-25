---
title: Erreur des outils Éditeur de liens LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: 363b6ef0ea9991ff5d657044282e99c558257fb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194627"
---
# <a name="linker-tools-error-lnk2023"></a>Erreur des outils Éditeur de liens LNK2023

dll ou point d’entrée incorrect \<la dll ou le point d’entrée >

L’éditeur de liens charge une version incorrecte de msobj90. dll. Vérifiez que Link. exe et msobj90. dll dans votre chemin d’accès ont la même version.

Une dépendance de msobj90. dll peut ne pas être présente. La liste de dépendances pour msobj90. dll est :

- Msvcr90. dll

- Kernel32.dll

Vérifiez sur votre ordinateur toutes les autres copies de msobj90. dll qui peuvent être obsolètes.
