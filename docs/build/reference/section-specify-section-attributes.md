---
description: En savoir plus sur:/SECTION (spécifier les attributs de section)
title: /SECTION (Spécifier les attributs de section)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8731f720e04ae2893f288e4b96aeaa019af43350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224788"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Spécifier les attributs de section)

> **/Section :**_nom_, [[**!**] {**DEKPRSW**}] [**, Align =**_Number_]

## <a name="remarks"></a>Notes

L’option **/section** modifie les attributs d’une section, en substituant les attributs définis lors de la compilation du fichier. obj de la section.

Une *section* dans un fichier exécutable portable (PE) est un bloc de mémoire contigu nommé qui contient du code ou des données. Certaines sections contiennent du code ou des données que votre programme a déclaré et utilise directement, tandis que d’autres sections de données sont créées pour vous par l’éditeur de liens et le gestionnaire de bibliothèque (lib.exe) et contiennent des informations vitales pour le système d’exploitation. Pour plus d’informations, consultez [format PE](/windows/win32/Debug/pe-format).

Spécifiez un signe deux-points ( :) et un *nom* de section. Le *nom* respecte la casse.

N’utilisez pas les noms suivants, car ils sont en conflit avec les noms standard. Par exemple,. sdata est utilisé sur les plateformes RISC :

- . Arch

- . BSS

- . Data

- .edata

- .idata

- . pdata

- . rdata

- . reloc

- . rsrc

- . sbss

- . sdata

- .srdata

- .text

- . XData

Spécifiez un ou plusieurs attributs pour la section. Les caractères d’attribut, répertoriés ci-dessous, ne respectent pas la casse. Vous devez spécifier tous les attributs que vous souhaitez appliquer à la section. un caractère d’attribut omis provoque la désactivation du bit d’attribut. Si vous ne spécifiez pas R, W ou E, l’état de lecture, d’écriture ou d’exécutable existant reste inchangé.

Pour nier un attribut, faites précéder son caractère d’un point d’exclamation ( !). Les significations des caractères d’attribut sont indiquées dans ce tableau :

|Caractère|Attribut|Signification|
|---------------|---------------|-------------|
|E|Execute|La section est exécutable|
|R|Lire|Autorise les opérations de lecture sur les données|
|W|Write|Autorise les opérations d’écriture sur les données|
|S|Partagé|Partage la section entre tous les processus qui chargent l’image|
|D|Pouvant être éliminée|Marque la section comme étant à ignorer|
|K|Pouvant être mis en cache|Marque la section comme ne pouvant pas être mise en cache|
|P|Paginable|Marque la section comme non paginable|

K et P sont inhabituels dans le sens où les indicateurs de section qui leur correspondent sont utilisés dans le sens négatif. Si vous spécifiez l’une d’entre elles sur la section. Text à l’aide de l’option **/section :. Text, K** , il n’y a aucune différence dans les indicateurs de section quand vous exécutez [DUMPBIN](dumpbin-options.md) avec l’option [/headers](headers.md) ; la section a déjà été mise en cache de manière implicite. Pour supprimer la valeur par défaut, spécifiez **/section :. Text, ! K** à la place. DUMPBIN révèle les caractéristiques de section, y compris « non mis en cache ».

Une section du fichier PE qui n’a pas de jeu E, R ou W n’est probablement pas valide.

L’argument **align =**_Number_ vous permet de spécifier une valeur d’alignement pour une section particulière. L’argument _Number_ est en octets et doit être une puissance de deux. Pour plus d’informations, consultez [/align](align-section-alignment.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Choisissez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option dans la zone **options supplémentaires** . Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
