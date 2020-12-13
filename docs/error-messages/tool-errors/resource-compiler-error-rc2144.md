---
description: 'En savoir plus sur : erreur du compilateur de ressources RC2144'
title: 'Erreur RC2144 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 8b40f989e4319b16a9a983f5e4e377aeb357e8f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133508"
---
# <a name="resource-compiler-error-rc2144"></a>Erreur RC2144 du compilateur de ressources 

L'ID DE LANGUE PRINCIPALE n'est pas un numéro

L'ID DE LANGUE PRINCIPALE doit être un ID de langue hexadécimal. Consultez [Chaînes de langues et de pays/régions](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) dans la *Référence de la bibliothèque Runtime* pour obtenir la liste des ID de langue valides.

Cette erreur peut aussi se produire si des ressources ont été ajoutées et supprimées à partir du fichier .RC à l'aide d'un outil. Pour résoudre ce problème, ouvrez le fichier .RC dans un éditeur de texte et nettoyez manuellement les ressources non utilisées.
