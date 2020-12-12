---
description: 'En savoir plus sur : isolation de la bibliothèque de contrôles communs MFC'
title: Isolement de la bibliothèque de contrôles communs MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
ms.openlocfilehash: f3e0f6ad981a690f6212455b8af891eaa97f2642
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335817"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Isolement de la bibliothèque de contrôles communs MFC

La bibliothèque de contrôles communs est maintenant isolée dans MFC, ce qui permet à différents modules (tels que les dll utilisateur) d’utiliser différentes versions de la bibliothèque de contrôles communs en spécifiant la version dans leurs manifestes.

Une application MFC (ou un code utilisateur appelé par MFC) appelle des API de bibliothèque de contrôles communs via des fonctions wrapper nommées `Afx` *nomfonction*, où *nomfonction* est le nom d’une API de contrôles communs. Ces fonctions wrapper sont définies dans afxcomctl32. h et afxcomctl32. inl.

Vous pouvez utiliser les macros [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) et [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) (définies dans afxcomctl32. h) pour déterminer si la bibliothèque de contrôles communs implémente une certaine API au lieu d’appeler [GetProcAddress](../build/getprocaddress.md).

Techniquement, vous effectuez des appels à des API de la bibliothèque de contrôles communs par le biais d’une classe wrapper `CComCtlWrapper` (définie dans afxcomctl32. h). `CComCtlWrapper` est également responsable du chargement et du déchargement de comctl32.dll. L’état du module MFC contient un pointeur vers une instance de `CComCtlWrapper` . Vous pouvez accéder à la classe wrapper à l’aide de la `afxComCtlWrapper` macro.

Notez que l’appel de l’API de contrôles communs directement (sans utiliser les fonctions wrapper MFC) à partir d’une application MFC ou d’une DLL utilisateur fonctionnera dans la plupart des cas, car l’application MFC ou la DLL utilisateur est liée à la bibliothèque de contrôles communs qu’elle a demandée dans son manifeste. Toutefois, le code MFC lui-même doit utiliser les wrappers, car le code MFC peut être appelé à partir de DLL utilisateur avec différentes versions de bibliothèque de contrôles communs.
