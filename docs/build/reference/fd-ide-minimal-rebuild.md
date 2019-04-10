---
title: /FD (Régénération minimale IDE)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424051"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Régénération minimale IDE)

**/FD** est exposé uniquement aux utilisateurs dans le [ligne de commande](command-line-property-pages.md) page de propriétés d’un C++ du projet **Pages de propriétés** boîte de dialogue. Il est disponible si et seulement si le déconseillées et désactivé par défaut [/Gm (activer la régénération minimale)](gm-enable-minimal-rebuild.md) option n’est pas sélectionnée. **/FD** n’a aucun effet autre que l’environnement de développement. **/FD** n’est pas exposé dans la sortie de `cl /?`.

Si vous n’activez pas déconseillées **/Gm** option dans l’environnement de développement **/FD** est utilisé. **/FD** garantit que le fichier .idb contient des informations de dépendance suffisantes. **/FD** est utilisée uniquement par l’environnement de développement, et elle ne doit pas être utilisée à partir de la ligne de commande ou un script de génération.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
