---
title: /ZH (algorithme de hachage pour le calcul de la somme de contrôle du fichier dans les informations de débogage)
description: Utilisez l’option de compilateur/ZH pour activer les sommes de contrôle de fichier source MD5, SHA-1 ou SHA-256 dans les informations de débogage
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686872"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH (algorithme de hachage pour le calcul de la somme de contrôle du fichier dans les informations de débogage)

Spécifie l’algorithme de hachage de chiffrement à utiliser pour générer une somme de contrôle de chaque fichier source.

## <a name="syntax"></a>Syntaxe

> **/ZH :** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>Arguments

**/ZH : MD5**\
Utilisez un hachage MD5 pour la somme de contrôle. Il s’agit de l’option par défaut.

**/ZH : SHA1**\
Utilisez un hachage SHA-1 pour la somme de contrôle.

**/ZH : SHA_256**\
Utilisez un hachage SHA-256 pour la somme de contrôle.

## <a name="remarks"></a>Notes

Les fichiers PDB stockent une somme de contrôle pour chaque fichier source compilé dans le code objet dans l’exécutable associé. La somme de contrôle permet au débogueur de vérifier que le code source qu’il charge correspond à l’exécutable. Le compilateur et le débogueur prennent en charge les algorithmes de hachage MD5, SHA-1 et SHA-256. Par défaut, le compilateur utilise un hachage MD5 pour générer la somme de contrôle. Vous pouvez spécifier cette option explicitement à l’aide de l’option **/zh : MD5** .

En raison d’un risque de problèmes de collision dans MD5 et SHA-1, Microsoft vous recommande d’utiliser l’option **/zh : SHA_256** . Le hachage SHA-256 peut entraîner une légère augmentation des temps de compilation.

Lorsque plusieurs options **/zh** sont spécifiées, la dernière option est utilisée.

L’option **/zh** est disponible à partir de Visual Studio 2019 version 16,4.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Modifiez la **propriété options supplémentaires** pour ajouter une **option/zh : MD5**, **/zh : SHA1**ou **/zh : SHA_256** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](compiler-options.md)\
[Serveur source](/windows/win32/debug/source-server-and-source-indexing)
