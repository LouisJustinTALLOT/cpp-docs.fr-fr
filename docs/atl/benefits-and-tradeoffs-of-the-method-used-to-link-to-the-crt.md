---
title: Avantages et inconvénients de la méthode utilisée pour le lien vers la bibliothèque CRT
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: b2e504de91cea9fef6e9acb0fc851bc2cc271e97
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221277"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Avantages et inconvénients de la méthode utilisée pour le lien vers la bibliothèque CRT

Votre projet peut lier avec la bibliothèque CRT de façon statique ou dynamique. Le tableau ci-dessous présente les avantages et les inconvénients liés à choix de la méthode à utiliser.

|Méthode|Avantage|Tradeoff|
|------------|-------------|--------------|
|Liaison statique à la bibliothèque CRT<br /><br /> (**Bibliothèque Runtime** définie sur **Single-threaded**)|La DLL CRT n’est pas requis sur le système où l’image s’exécutera.|Environ 25 Ko de code de démarrage est ajouté à votre image, augmenter sa taille.|
|Liaison dynamique vers le CRT<br /><br /> (**Bibliothèque Runtime** définie sur **multithread**)|Votre image ne nécessite pas le code de démarrage du CRT, par conséquent, il est beaucoup plus petite.|La DLL CRT doit être sur le système de l’image en cours d’exécution.|

La rubrique [au CRT dans votre projet ATL](../atl/linking-to-the-crt-in-your-atl-project.md) explique comment sélectionner le mode de liaison vers la bibliothèque CRT.

## <a name="see-also"></a>Voir aussi

[Programmation avec ATL et le code C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL et comportement de la bibliothèque runtime Visual C++](../build/run-time-library-behavior.md)<br/>
[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)
