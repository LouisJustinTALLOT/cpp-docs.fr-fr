---
description: 'En savoir plus sur : erreur mathématique mathématique M6202'
title: Erreur mathématique M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: f6d4c9c8abab59708854eaac6763181018f47473
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244301"
---
# <a name="math-error-m6202"></a>Erreur mathématique M6202

'fonction' : erreur _SING

Un argument de la fonction donnée était une valeur de singularité pour cette fonction. La fonction n’est pas définie pour cet argument.

Cette erreur appelle la `_matherr` fonction avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.
