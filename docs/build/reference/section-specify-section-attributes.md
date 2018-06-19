---
title: /SECTION (spécifier les attributs de Section) | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9b0a724f0e9156c81db20bf283e4418dd2f22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379521"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Spécifier les attributs de section)

> **/ SECTION :**_nom_, [[**!**] {**DEKPRSW**}] [**, aligner =**_nombre_]

## <a name="remarks"></a>Notes

Le **/SECTION** option modifie les attributs d’une section, en substituant les attributs définis lorsque le fichier .obj de la section a été compilé.

A *section* dans un exécutable portable (PE) le fichier est un bloc de mémoire qui contient le code ou des données contiguë nommé. Certaines sections contiennent le code ou les données que votre programme déclaré et utilise directement, alors que les autres sections de données sont créées pour vous par le Gestionnaire de bibliothèque (lib.exe) et de l’éditeur de liens et contiennent des informations essentielles pour le système d’exploitation. Pour plus d’informations, consultez [Format PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

Spécifiez un signe deux-points ( :) et une section *nom*. Le *nom* respecte la casse.

N’utilisez pas les noms suivants, car ils sont en conflit avec des noms standards. Par exemple, .sdata est utilisé sur les plateformes RISC :

- .arch

- .BSS

- .Data

- .edata

- .iData

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .Text

- .XData

Spécifiez un ou plusieurs attributs de la section. Les caractères de l’attribut, répertoriés ci-dessous, ne respectent pas la casse. Vous devez spécifier tous les attributs de la section ; un caractère d’attribut est omis provoque la mise hors tension du bit d’attribut. Si vous ne spécifiez pas R, W ou E, existant en lecture, écriture, ou état exécutable demeure inchangée.

Pour exclure un attribut, faites précéder son caractère avec un point d’exclamation ( !). La signification des caractères d’attribut est répertoriée dans ce tableau :

|Caractère|Attribut|Signification|
|---------------|---------------|-------------|
|E|Exécuter|La section est exécutable.|
|R|Lecture|Permet les opérations de lecture sur les données|
|W|Write|Permet les opérations d’écriture sur les données|
|S|Partagé|Partage la section parmi tous les processus qui chargent l’image|
|D|pouvant être éliminée|Marque la section comme pouvant être supprimée|
|K|Mise en cache|Marque la section comme ne pouvant pas être mises|
|P|Paginable|Marque la section comme non paginable|

K et P est rares, les indicateurs de section correspondants sont utilisés dans le sens négatif. Si vous spécifiez un d’eux dans la section .text à l’aide de la **/section :.Text, K** option, il n’existe aucune différence dans les indicateurs de section lorsque vous exécutez [DUMPBIN](../../build/reference/dumpbin-options.md) avec la [/HEADERS](../../build/reference/headers.md)option ; la section déjà implicitement mis en cache. Pour supprimer la valeur par défaut, spécifiez   **/section :.Text, ! K** à la place. DUMPBIN révèle les caractéristiques de la section, y compris « Non mis en cache. »

Une section dans le fichier PE qui n’a pas de E, R ou W défini est probablement non valide.

Le **ALIGN =**_nombre_ argument vous permet de spécifier une valeur d’alignement pour une section donnée. Le _nombre_ argument est exprimée en octets et doit être une puissance de deux. Consultez [/ALIGN](../../build/reference/align-section-alignment.md) pour plus d’informations.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)  
[Options de l’éditeur de liens](../../build/reference/linker-options.md)  
