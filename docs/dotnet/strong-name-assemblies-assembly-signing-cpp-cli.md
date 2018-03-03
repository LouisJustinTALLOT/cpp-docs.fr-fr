---
title: "Assemblys de nom fort (signature d’Assembly) (C + c++ / CLI) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2099389131145838a70b579053c65698dbc3a857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Assemblys de nom fort (signature d'assembly) (C++/CLI)
Cette rubrique explique comment vous pouvez signer un assembly, souvent appelé donner votre assembly un nom fort.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez Visual C++, utilisez les options de l’éditeur de liens pour signer votre assembly pour éviter les problèmes liés aux attributs CLR de signature d’assembly :  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Les raisons pour ne pas utiliser les attributs incluent le fait que le nom de clé est visible dans les métadonnées de l’assembly, qui peuvent être un risque de sécurité si le nom de fichier consacrée des informations confidentielles. En outre, le processus de génération utilisé par l’environnement de développement Visual C++ invalidera la clé avec laquelle l’assembly est signé si vous utilisez des attributs CLR pour attribuer un nom fort à un assembly, puis exécutez un outil de post-traitement tel que mt.exe sur l’assembly.  
  
 Si vous générez à partir de la ligne de commande, utilisez les options de l’éditeur de liens pour signer votre assembly, puis exécutez un outil de post-traitement (comme mt.exe), vous devez signer à nouveau l’assembly avec sn.exe. Vous pouvez également générer et différer la signature de l’assembly et après l’exécution des outils de post-traitement, complétez la signature.  
  
 Si vous utilisez les attributs de signature lors de la génération dans l’environnement de développement, vous pouvez signer correctement l’assembly en appelant explicitement sn.exe ([Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool)) dans un événement post-build. Pour plus d’informations, consultez [spécifiant les événements de Build](../ide/specifying-build-events.md). Les durées de génération peuvent être inférieure si vous utilisez des attributs et un événement post-build, par rapport à l’aide des options d’un éditeur de liens.  
  
 Les options de l’éditeur de liens suivantes prennent en charge la signature d’assembly :  
  
-   [/DELAYSIGN (signer partiellement un Assembly)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE (spécifier la clé ou une paire de clés pour signer un Assembly)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER (spécifier un conteneur de clé pour signer un Assembly)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Pour plus d’informations sur les assemblys forts, consultez [création et assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)