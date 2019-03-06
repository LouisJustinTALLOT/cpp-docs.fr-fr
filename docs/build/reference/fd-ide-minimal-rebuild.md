---
title: /FD (Régénération minimale IDE)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 0685df0baf14685bd24b8390dd58b382ae5ac506
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422050"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Régénération minimale IDE)

**/FD** n’est pas exposée aux utilisateurs, sauf dans le [ligne de commande](../../ide/command-line-property-pages.md) page de propriétés d’un projet C++ **Pages de propriétés** boîte de dialogue si et seulement si [/Gm (activer la régénération minimale)](../../build/reference/gm-enable-minimal-rebuild.md) n’est pas également sélectionné. **/FD** n’a aucun effet autre que l’environnement de développement. **/FD** n’est pas exposée dans la sortie de **cl / ?**.

Si vous n’activez pas **/Gm** dans l’environnement de développement **/FD** sera utilisé. **/FD** garantit que le fichier .idb dispose de suffisamment d’informations dépendance. **/FD** est utilisée uniquement par l’environnement de développement, et il ne doit pas être utilisé à partir de la ligne de commande ou un script de génération.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
