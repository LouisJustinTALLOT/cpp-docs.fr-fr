---
title: Événements de build distants (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 1e5c453da05fe65871fa7f6b0d4ca6528a96d4dd
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821476"
---
# <a name="build-event-properties-linux-c"></a>Événement de build, propriétés (Linux C++)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Événement prébuild

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="pre-link-event"></a>Événement de préédition des liens

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter.
Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="post-build-event"></a>Événement post-build

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement postbuild à exécuter.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

## <a name="remote-pre-build-event"></a>Événement prébuild distant

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

## <a name="remote-pre-link-event"></a>Événement de préédition des liens distant

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

## <a name="remote-post-build-event"></a>Événement post-build distant

Property | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement post-build à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

::: moniker-end


