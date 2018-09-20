---
title: Bibliothèque de contrôles d’isolation de MFC courantes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3189b2e3db594801fe417ca43867da7db2e18fd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423778"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Isolement de la bibliothèque de contrôles communs MFC

La bibliothèque de contrôles communs est désormais isolée dans MFC, ce qui permet de différents modules (par exemple, utilisateur DLL) à utiliser différentes versions de la bibliothèque de contrôles communs en spécifiant la version dans leur manifeste.

Une application MFC (ou le code utilisateur appelée par MFC) effectue des appels à la bibliothèque de contrôles communs API via les fonctions wrapper nommé `Afx` *FunctionName*, où *FunctionName* est le nom d’un commun API de contrôles. Ces fonctions wrapper sont définies dans afxcomctl32.h et afxcomctl32.inl.

Vous pouvez utiliser la [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) et [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) macros (définies dans afxcomctl32.h) pour déterminer si la bibliothèque de contrôles communs implémente une certaine API au lieu d’appeler [GetProcAddress](../build/getprocaddress.md).

Techniquement, vous effectuer des appels aux API de bibliothèque de contrôles courants via une classe wrapper, `CComCtlWrapper` (définies dans afxcomctl32.h). `CComCtlWrapper` est également responsable du chargement et déchargement de comctl32.dll. L’état du Module MFC contient un pointeur vers une instance de `CComCtlWrapper`. Vous pouvez accéder à la classe wrapper à l’aide du `afxComCtlWrapper` (macro).

Notez que l’appel des API de contrôles courants directement (sans utiliser les fonctions de wrapper MFC) à partir d’une MFC application ou DLL utilisateur fonctionnera dans la plupart des cas, car l’application MFC ou l’utilisateur DLL est liée à la bibliothèque de contrôles communs elles demandées dans son manifeste). Toutefois, le code MFC elle-même doit utiliser les wrappers, étant donné que le code MFC peut être appelée à partir de DLL utilisateur avec différentes versions de bibliothèque de contrôles communs.

