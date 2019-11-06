---
title: Erreur d’optimisation guidée par profil PG0165
description: Décrit les erreurs de PG0165 dans la lecture des données de l’optimisation guidée par profil (PGO).
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626799"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Erreur d’optimisation guidée par profil PG0165

Une erreur s’est produite lors de la lecture des données d’optimisation guidée par profil. Cette erreur peut se présenter sous plusieurs formes :

> Lecture de'*nom_fichier. pgd*' : 'version de PGD non prise en charge (incompatibilité de version) '.

Les fichiers PGD sont spécifiques à un ensemble d’outils de compilateur particulier. Cette erreur est générée lorsque vous utilisez un compilateur différent de celui utilisé pour créer *filename. pgd*. L’erreur indique que cet ensemble d’outils du compilateur ne peut pas utiliser les données de *filename. pgd* pour optimiser le programme en cours. Pour résoudre ce problème, régénérez le *fichier filename*. pgd à l’aide de l’ensemble d’outils du compilateur actuel.

> Lecture de'*nom_fichier. pgd*' : 'le fichier PGD est en lecture seule'.

Cette erreur s’affiche lorsque le fichier PGD est marqué en lecture seule sur le système de fichiers. Pour résoudre ce problème, modifiez les attributs de fichier en lecture-écriture.
