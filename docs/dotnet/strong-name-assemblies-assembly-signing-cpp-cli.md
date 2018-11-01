---
title: Assemblys de nom fort (signature d'assembly) (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: c23c3b70a2152fbceb771e085b73d7daf7aa3c2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527554"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Assemblys de nom fort (signature d'assembly) (C++/CLI)

Cette rubrique explique comment vous pouvez signer votre assembly, souvent appelée attribution un nom fort d'à votre assembly.

## <a name="remarks"></a>Notes

Lorsque vous utilisez Visual C++, utilisez les options de l’éditeur de liens pour signer votre assembly pour éviter les problèmes liés aux attributs CLR pour la signature d’assembly :

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

Les raisons pour ne pas utiliser les attributs incluent le fait que le nom de clé est visible dans les métadonnées de l’assembly, qui peuvent être un risque de sécurité si le nom de fichier consacrée des informations confidentielles. En outre, le processus de génération utilisé par l’environnement de développement Visual C++ invalidera la clé avec laquelle l’assembly est signé si vous utilisez des attributs CLR pour attribuer un nom fort à un assembly, puis exécutez un outil de post-traitement tel que mt.exe sur l’assembly.

Si vous générez en ligne de commande, utilisez les options de l’éditeur de liens pour signer votre assembly, puis exécutez un outil de post-traitement (comme mt.exe), vous devez signer à nouveau l’assembly avec sn.exe. Vous pouvez également générer et différer la signature de l’assembly et après l’exécution des outils de post-traitement, complétez la signature.

Si vous utilisez les attributs de signature lors de la génération dans l’environnement de développement, vous pouvez vous connecter l’assembly en appelant explicitement sn.exe ([Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool)) dans un événement post-build. Pour plus d’informations, consultez [Spécification d’événements de build](../ide/specifying-build-events.md). Durées de génération peuvent être inférieure si vous utilisez des attributs et un événement post-build, par rapport à l’aide des options d’un éditeur de liens.

Les options de l’éditeur de liens suivantes prennent en charge la signature d’assembly :

- [/DELAYSIGN (Signer partiellement un assembly)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (Spécifier une clé ou une paire de clés pour signer un assembly)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (Spécifier un conteneur de clé pour signer un assembly)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Pour plus d’informations sur les assemblys forts, consultez [création et assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)