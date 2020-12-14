---
description: 'En savoir plus sur : erreur irrécupérable du compilateur de ressources RC1052 du compilateur'
title: 'Erreur irrécupérable RC1052 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: 41ef30cfde7d463337b1747b3f6141866e39e3be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255078"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Erreur irrécupérable RC1052 du compilateur de ressources 

limite du compilateur : blocs #if ou #ifdef imbriqués trop profondément

Le programme a dépassé le nombre maximal de niveaux d'imbrication autorisés pour les directives `#if` et `#ifdef`.

Cette erreur peut être provoquée par des fichiers include qui utilisent ces directives de préprocesseur.

Pour résoudre ce problème, réduisez le nombre de directives `#if` et `#ifdef` imbriquées dans votre fichier de ressources. Si le problème est provoqué par les fichiers d'en-tête inclus dans votre fichier de ressources, réduisez le nombre de directives `#if` et `#ifdef` imbriquées dans les fichiers d'en-tête. Si ce n'est pas possible, créez un fichier d'en-tête et incluez-le dans votre fichier de ressources, en exécutant le préprocesseur sur les fichiers d'en-tête inclus existants. Pour plus d’informations, consultez l’option de compilateur [/p (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) .
