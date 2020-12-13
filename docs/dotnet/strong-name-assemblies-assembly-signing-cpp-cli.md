---
description: 'En savoir plus sur : assemblys de nom fort (signature d’assembly) (C++/CLI)'
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
ms.openlocfilehash: 9fc08df759fa384ed13dbe3d8c3eb2d843183517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335317"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Assemblys de nom fort (signature d'assembly) (C++/CLI)

Cette rubrique explique comment vous pouvez signer votre assembly, souvent appelé donner un nom fort à votre assembly.

## <a name="remarks"></a>Notes

Quand vous utilisez Visual C++, utilisez les options de l’éditeur de liens pour signer votre assembly afin d’éviter les problèmes liés aux attributs CLR pour la signature de l’assembly :

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

Les raisons pour lesquelles vous n’utilisez pas les attributs incluent le fait que le nom de clé est visible dans les métadonnées de l’assembly, ce qui peut constituer un risque pour la sécurité si le nom de fichier inclut des informations confidentielles. En outre, le processus de génération utilisé par l’environnement de développement Visual C++ invalidera la clé avec laquelle l’assembly est signé si vous utilisez des attributs CLR pour attribuer un nom fort à un assembly, puis exécutez un outil de publication comme mt.exe sur l’assembly.

Si vous générez à partir de la ligne de commande, utilisez les options de l’éditeur de liens pour signer votre assembly, puis exécutez un outil de postérieur au traitement (comme mt.exe), vous devrez signer à nouveau l’assembly avec sn.exe. Vous pouvez également générer et différer la signature de l’assembly et, après avoir exécuté les outils de surtraitement, terminer la signature.

Si vous utilisez les attributs de signature lors de la génération dans l’environnement de développement, vous pouvez signer correctement l’assembly en appelant explicitement sn.exe ([Sn.exe (outil Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool)) dans un événement après génération. Pour plus d’informations, consultez [Spécification d’événements de build](../build/specifying-build-events.md). Les durées de génération peuvent être inférieures si vous utilisez des attributs et un événement après génération, par rapport à l’utilisation des options de l’éditeur de liens.

Les options de l’éditeur de liens suivantes prennent en charge la signature d’assembly :

- [/DELAYSIGN (signer partiellement un assembly)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (spécifier une clé ou une paire de clés pour signer un assembly)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (spécifier un conteneur de clé pour signer un assembly)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Pour plus d’informations sur les assemblys forts, consultez [création et utilisation d’assemblys Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
