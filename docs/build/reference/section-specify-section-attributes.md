---
title: /SECTION (spécifier les attributs de Section) | Microsoft Docs
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
ms.openlocfilehash: 1f052d8acaceee88b6b9a727e176666180b1bb9d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214178"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Spécifier les attributs de section)

> **/ SECTION :**_nom_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_nombre_]

## <a name="remarks"></a>Notes

Le **/SECTION** option modifie les attributs d’une section, en substituant les attributs définis lorsque le fichier .obj de la section a été compilé.

Un *section* dans un exécutable portable (PE) le fichier est un bloc nommé contiguë de mémoire qui contient le code ou des données. Certaines sections contiennent des codes ou des données que votre programme déclaré et utilise directement, alors que les autres sections de données sont créées pour vous par l’éditeur de liens et le Gestionnaire de bibliothèque (lib.exe) et contiennent des informations vitales pour le système d’exploitation. Pour plus d’informations, consultez [Format PE](/windows/desktop/Debug/pe-format).

Spécifiez un signe deux-points ( :) et une section *nom*. Le *nom* respecte la casse.

N’utilisez pas les noms suivants, car ils sont en conflit avec des noms standard. Par exemple, .sdata est utilisé sur les plateformes RISC :

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

- ".Text"

- .XData

Spécifiez un ou plusieurs attributs de la section. Les caractères de l’attribut, répertoriés ci-après, ne respectent pas la casse. Vous devez spécifier tous les attributs de la section d’avoir ; un caractère d’attribut est omis provoque le bit d’attribut soit désactivé. Si vous ne spécifiez pas de R, W ou E, existant en lecture, écriture ou exécutable état reste inchangé.

Pour exclure un attribut, faites précéder son caractère avec un point d’exclamation ( !). Les significations des caractères d’attribut sont affichées dans ce tableau :

|Caractère|Attribut|Signification|
|---------------|---------------|-------------|
|E|Exécuter|La section est exécutable.|
|R|Lecture|Permet les opérations de lecture sur les données|
|W|Write|Autorise les opérations d’écriture sur les données|
|S|Partagé|Partage la section entre tous les processus qui chargent l’image|
|D|Pouvant être éliminée|Marque la section comme pouvant être éliminée|
|K|Être mis en cache|Marque la section comme non mis en cache|
|P|Paginable|Marque la section comme non paginable|

K et P est inhabituels, les indicateurs de la section qui leur correspondent sont utilisés dans le sens négatif. Si vous spécifiez un d’eux dans la section ".Text" à l’aide de la **/section :.Text, K** , il n’existe aucune différence dans les indicateurs de section lorsque vous exécutez l’option [DUMPBIN](../../build/reference/dumpbin-options.md) avec la [/HEADERS](../../build/reference/headers.md)option ; la section a été déjà implicitement mis en cache. Pour supprimer la valeur par défaut, spécifiez   **/section :.Text, ! K** à la place. DUMPBIN révèle les caractéristiques de section, y compris « Non mis en cache. »

Une section dans le fichier PE qui n’a pas de E, R ou W définie est probablement non valide.

Le **ALIGN =**_nombre_ argument vous permet de spécifier une valeur d’alignement pour une section donnée. Le _nombre_ argument est exprimée en octets et doit être une puissance de deux. Consultez [/aligner](../../build/reference/align-section-alignment.md) pour plus d’informations.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)  
[Options de l’éditeur de liens](../../build/reference/linker-options.md)  
