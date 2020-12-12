---
description: 'En savoir plus sur : erreur irrécupérable C1305'
title: Erreur irrécupérable C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 100046d5ad7c6fa943358063d3d3cb21ffa00e5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267896"
---
# <a name="fatal-error-c1305"></a>Erreur irrécupérable C1305

la base de données de profils’pgd_file’est pour une architecture différente

Un fichier. pgd qui a été généré à partir de l’opération/LTCG : PGINSTRUMENT pour une autre plateforme a été passé à [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . Les [optimisations guidées par profil](../../build/profile-guided-optimizations.md) sont disponibles pour les plateformes x86 et x64. Toutefois, un fichier. pgd généré avec une opération/LTCG : PGINSTRUMENT pour une plateforme n’est pas valide en tant qu’entrée dans/LTCG : PGOPTIMIZE pour une plateforme différente.

Pour résoudre cette erreur, transmettez uniquement un fichier. pgd créé avec/LTCG : PGINSTRUMENT à/LTCG : PGOPTIMIZE sur la même plateforme.
