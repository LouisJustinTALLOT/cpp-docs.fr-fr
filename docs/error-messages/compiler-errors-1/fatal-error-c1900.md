---
title: Erreur irrécupérable C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165721"
---
# <a name="fatal-error-c1900"></a>Erreur irrécupérable C1900

> Incompatibilité de il entre '*tool1*'version'*number1*'et'*tool2*'version'*number2*'

Les outils exécutés dans différentes passes du compilateur ne correspondent pas. *number1* et *number2* font référence aux dates sur les fichiers. Par exemple, dans la passe 1, le compilateur frontal s'exécute (c1.dll), alors que dans la passe 2, c'est le compilateur principal (c2.dll). Les dates doivent correspondre dans les fichiers.

Pour résoudre ce problème, assurez-vous que toutes les mises à jour ont été appliquées à Visual Studio. Si le problème persiste, utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.