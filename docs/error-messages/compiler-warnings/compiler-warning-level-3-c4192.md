---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4192'
title: Avertissement du compilateur (niveau 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 8cfebf1845c578723bab5622e18699c0282d4c4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344222"
---
# <a name="compiler-warning-level-3-c4192"></a>Avertissement du compilateur (niveau 3) C4192

exclusion automatique de’name’lors de l’importation de la bibliothèque de types’Library'

Une `#import` bibliothèque contient un élément, un *nom*, qui est également défini dans les en-têtes système Win32. En raison des limitations des bibliothèques de types, les noms tels que **IUnknown** ou GUID sont souvent définis dans une bibliothèque de types, en dupliquant la définition des en-têtes système. `#import` détecte ces éléments et refuse de les incorporer dans les fichiers d’en-tête. tlh et. tli.

Pour remplacer ce comportement, utilisez `#import` les attributs [no_auto_exclude](../../preprocessor/no-auto-exclude.md) et [include ()](../../preprocessor/include-parens.md).
