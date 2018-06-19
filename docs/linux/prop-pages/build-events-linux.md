---
title: Événements de build distants (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 38c036bf747115823b853d0d66077f4402a7f7ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338404"
---
# <a name="build-event-properties-linux-c"></a>Événement de build, propriétés (Linux C++) 

## <a name="pre-build-event"></a>Événement prébuild

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="pre-link-event"></a>Événement de préédition des liens

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter.
Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="post-build-event"></a>Événement post-build

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement postbuild à exécuter.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="remote-pre-build-event"></a>Événement prébuild distant

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

## <a name="remote-pre-link-event"></a>Événement de préédition des liens distant

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

## <a name="remote-post-build-event"></a>Événement post-build distant

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement post-build à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.
