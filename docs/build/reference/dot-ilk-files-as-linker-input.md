---
description: En savoir plus sur :. Fichiers ilk en tant qu’entrée dans l’éditeur de liens
title: Fichiers .ilk en tant qu'entrée dans l'éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 0aaa5fac19cedb8d94fc6dc9ab03a0f23fa0e49b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192731"
---
# <a name="ilk-files-as-linker-input"></a>Fichiers .ilk en tant qu'entrée dans l'éditeur de liens

Lors de la liaison incrémentielle, LINK met à jour le fichier d’État. ilk qu’il a créé au cours du premier lien incrémentiel. Ce fichier a le même nom de base que le fichier. exe ou. dll, et son extension est. ilk. Lors des liens incrémentiels suivants, LINK met à jour le fichier. ilk. Si le fichier. ilk est manquant, LINK effectue un lien complet et crée un nouveau fichier. ilk. Si le fichier. ilk est inutilisable, LINK effectue un lien non incrémentiel. Pour plus d’informations sur les liens incrémentiels, consultez l’option [Link Incremental (/Incremental)](incremental-link-incrementally.md) .

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée de lien](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
