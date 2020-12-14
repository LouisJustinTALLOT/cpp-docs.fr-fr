---
description: 'En savoir plus sur : erreur irrécupérable C1900'
title: Erreur irrécupérable C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: e7bcd44846f34b3d3910d4c1aac292ee6414b439
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276112"
---
# <a name="fatal-error-c1900"></a>Erreur irrécupérable C1900

> Incompatibilité il entre'*Tool1*'version'*nombre1*'et'*tool2*'version'*nombre2*'

Les outils exécutés dans différentes passes du compilateur ne correspondent pas. *nombre1* et *nombre2* font référence aux dates des fichiers. Par exemple, dans la passe 1, le compilateur frontal s'exécute (c1.dll), alors que dans la passe 2, c'est le compilateur principal (c2.dll). Les dates doivent correspondre dans les fichiers.

Pour résoudre ce problème, assurez-vous que toutes les mises à jour ont été appliquées à Visual Studio. Si le problème persiste, utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.
