---
description: En savoir plus sur les avantages et les inconvénients de la méthode utilisée pour établir un lien vers la bibliothèque CRT
title: Avantages et inconvénients de la méthode utilisée pour établir un lien vers la bibliothèque CRT
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: 763332de9615e978d84902f67f2c97efd0767c89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148523"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Avantages et inconvénients de la méthode utilisée pour établir un lien vers la bibliothèque CRT

Votre projet peut être lié au CRT de manière dynamique ou statique. Le tableau ci-dessous décrit les avantages et les compromis impliqués dans le choix de la méthode à utiliser.

|Méthode|Avantage|Compromis|
|------------|-------------|--------------|
|Liaison statique au CRT<br /><br /> (La **bibliothèque Runtime** est définie sur un **thread unique**)|La DLL CRT n’est pas requise sur le système sur lequel l’image s’exécutera.|Environ 25 Ko de code de démarrage sont ajoutés à votre image, ce qui accroît considérablement sa taille.|
|Liaison dynamique au CRT<br /><br /> (La **bibliothèque Runtime** est définie sur **multithread**)|Votre image ne nécessite pas le code de démarrage du CRT, il est donc nettement plus petit.|La DLL CRT doit se trouver sur le système qui exécute l’image.|

La rubrique [liaison au CRT dans votre projet ATL](../atl/linking-to-the-crt-in-your-atl-project.md) explique comment sélectionner la manière de créer un lien vers le CRT.

## <a name="see-also"></a>Voir aussi

[Programmation avec des Run-Time du code ATL et C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL et comportement de la bibliothèque runtime Visual C++](../build/run-time-library-behavior.md)<br/>
[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
