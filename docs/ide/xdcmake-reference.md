---
title: Référence XDCMake | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- xdcmake
dev_langs:
- C++
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf28f01778bea31bc84a57fa74fed3221673dec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039957"
---
# <a name="xdcmake-reference"></a>Référence XDCMake
xdcmake.exe est un programme qui compile les fichiers .xdc en fichier .xml. Un fichier .xdc est créé par le compilateur Visual C++ pour chaque fichier de code source quand le code source est compilé avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) et que le fichier de code source contient des commentaires de documentation marqués avec des balises XML.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Pour utiliser xdcmake.exe dans l’environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
2.  Ouvrez le dossier **Propriétés de configuration**.  
  
3.  Cliquez sur la page de propriétés **Commentaires de document XML**.  
  
> [!NOTE]
>  Les options de xdcmake.exe au niveau de la ligne de commande diffèrent des options de xdcmake.exe quand celui-ci est utilisé dans l’environnement de développement (pages de propriétés). Pour plus d’informations sur l’utilisation de xdcmake.exe dans l’environnement de développement, consultez [Outil Générateur de documents XML, page de propriétés](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Syntaxe  
 xdcmake `input_filename options`  
  
## <a name="parameters"></a>Paramètres  
  
*input_filename*<br/>
Nom de fichier des fichiers .xdc utilisés comme entrée pour xdcmake.exe. Spécifiez un ou plusieurs fichiers .xdc, ou utilisez *.xdc pour employer tous les fichiers .xdc dans le répertoire actif.  
  
*options*<br/>
Zéro ou plusieurs des éléments suivants :  
  
|Option|Description|  
|------------|-----------------|  
|/?, /help|Affiche l’aide pour xdcmake.exe.|  
|/assembly:*nomfichier*|Vous permet de spécifier la valeur de la balise \<assembly> dans le fichier .xml.  Par défaut, la valeur de la balise \<assembly> est identique au nom du fichier .xml.|  
|/nologo|Supprime le message de copyright.|  
|/out:*nomfichier*|Vous permet de spécifier le nom du fichier .xml.  Par défaut, le nom du fichier .xml est le nom du premier fichier .xdc traité par xdcmake.exe.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio appelle xdcmake.exe automatiquement lors de la génération d’un projet. Vous pouvez également appeler xdcmake.exe à partir de la ligne de commande.  
  
 Consultez [Balises recommandées pour les commentaires de documentation](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) pour plus d’informations sur l’ajout de commentaires de documentation aux fichiers de code source.  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)