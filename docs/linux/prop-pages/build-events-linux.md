---
description: 'En savoir plus sur : propriétés des événements de build (Linux C++)'
title: Événements de build distants (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: f134a882202881b1b89230459cc21c1b9757f6db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169812"
---
# <a name="build-event-properties-linux-c"></a>Événement de build, propriétés (Linux C++)

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="pre-build-event"></a>Événement prébuild

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter. |
| Description | Spécifie une description de l’outil d’événement prébuild à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Spécifiez éventuellement des paires de mappage local à distant à l’aide d’une syntaxe similaire à celle-ci : fulllocalpath1 : = fullremotepath1 ; fulllocalpath2 : = fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant. |

## <a name="pre-link-event"></a>Événement de préédition des liens

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter. |
| Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Spécifiez éventuellement des paires de mappage local à distant à l’aide d’une syntaxe similaire à celle-ci : fulllocalpath1 : = fullremotepath1 ; fulllocalpath2 : = fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant. |

## <a name="post-build-event"></a>Événement post-build

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement postbuild à exécuter. |
| Description | Spécifie une description de l’outil d’événement post-build à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Spécifiez éventuellement des paires de mappage local à distant à l’aide d’une syntaxe similaire à celle-ci : fulllocalpath1 : = fullremotepath1 ; fulllocalpath2 : = fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant. |

## <a name="remote-pre-build-event"></a>Événement prébuild distant

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter sur le système distant. |
| Description | Spécifie une description de l’outil d’événement prébuild à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Si vous le souhaitez, vous pouvez spécifier des paires de mappage distant à local à l’aide de la syntaxe suivante : fullremotepath1 : = fulllocalpath1 ; fullremotepath2 : = fulllocalpath2, où un fichier distant peut être copié à l’emplacement spécifié sur l’ordinateur local. |

## <a name="remote-pre-link-event"></a>Événement de préédition des liens distant

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement de préédition des liens à exécuter sur le système distant. |
| Description | Spécifie une description de l’outil d’événement de préédition des liens à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Si vous le souhaitez, vous pouvez spécifier des paires de mappage distant à local à l’aide de la syntaxe suivante : fullremotepath1 : = fulllocalpath1 ; fullremotepath2 : = fulllocalpath2, où un fichier distant peut être copié à l’emplacement spécifié sur l’ordinateur local. |

## <a name="remote-post-build-event"></a>Événement post-build distant

| Propriété | Description |
|--|--|
| Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement post-build à exécuter sur le système distant. |
| Description | Spécifie une description de l’outil d’événement post-build à afficher. |
| Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle. |
| Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Si vous le souhaitez, vous pouvez spécifier des paires de mappage distant à local à l’aide de la syntaxe suivante : fullremotepath1 : = fulllocalpath1 ; fullremotepath2 : = fulllocalpath2, où un fichier distant peut être copié à l’emplacement spécifié sur l’ordinateur local. |

::: moniker-end
