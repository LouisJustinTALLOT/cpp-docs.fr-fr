---
title: /SECTION (Spécifier les attributs de section)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8fb73043c9c185adee0859bb81098eab022430c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318561"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Spécifier les attributs de section)

> **/ SECTION :**_nom_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_nombre_]

## <a name="remarks"></a>Notes

Le **/SECTION** option modifie les attributs d’une section, en substituant les attributs définis lorsque le fichier .obj de la section a été compilé.

Un *section* dans un exécutable portable (PE) le fichier est un bloc nommé contiguë de mémoire qui contient le code ou des données. Certaines sections contiennent des codes ou des données que votre programme déclaré et utilise directement, alors que les autres sections de données sont créées pour vous par l’éditeur de liens et le Gestionnaire de bibliothèque (lib.exe) et contiennent des informations vitales pour le système d’exploitation. Pour plus d’informations, consultez [Format PE](/windows/desktop/Debug/pe-format).

Spécifiez un signe deux-points ( :) et une section *nom*. Le *nom* respecte la casse.

N’utilisez pas les noms suivants, car ils sont en conflit avec des noms standard. Par exemple, .sdata est utilisé sur les plateformes RISC :

- .arch

- .bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

Spécifiez un ou plusieurs attributs de la section. Les caractères de l’attribut, répertoriés ci-après, ne respectent pas la casse. Vous devez spécifier tous les attributs de la section d’avoir ; un caractère d’attribut est omis provoque le bit d’attribut soit désactivé. Si vous ne spécifiez pas de R, W ou E, existant en lecture, écriture ou exécutable état reste inchangé.

Pour exclure un attribut, faites précéder son caractère avec un point d’exclamation ( !). Les significations des caractères d’attribut sont affichées dans ce tableau :

|Caractère|Attribut|Signification|
|---------------|---------------|-------------|
|E|Exécuter|La section est exécutable.|
|R|Lecture|Permet les opérations de lecture sur les données|
|W|Write|Autorise les opérations d’écriture sur les données|
|S|Shared|Partage la section entre tous les processus qui chargent l’image|
|D|Pouvant être éliminée|Marque la section comme pouvant être éliminée|
|K|Être mis en cache|Marque la section comme non mis en cache|
|P|Paginable|Marque la section comme non paginable|

K et P est inhabituels, les indicateurs de la section qui leur correspondent sont utilisés dans le sens négatif. Si vous spécifiez un d’eux dans la section ".Text" à l’aide de la **/section :.Text, K** , il n’existe aucune différence dans les indicateurs de section lorsque vous exécutez l’option [DUMPBIN](dumpbin-options.md) avec la [/HEADERS](headers.md)option ; la section a été déjà implicitement mis en cache. Pour supprimer la valeur par défaut, spécifiez   **/section :.Text, ! K** à la place. DUMPBIN révèle les caractéristiques de section, y compris « Non mis en cache. »

Une section dans le fichier PE qui n’a pas de E, R ou W définie est probablement non valide.

Le **ALIGN =**_nombre_ argument vous permet de spécifier une valeur d’alignement pour une section donnée. Le _nombre_ argument est exprimée en octets et doit être une puissance de deux. Consultez [/aligner](align-section-alignment.md) pour plus d’informations.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
