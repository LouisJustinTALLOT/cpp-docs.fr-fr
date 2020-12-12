---
description: 'En savoir plus sur : référence XDCMake'
title: Référence XDCMake
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: c9e597828ca37b67a21a5b2f442fffcac001b541
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260993"
---
# <a name="xdcmake-reference"></a>Référence XDCMake

xdcmake.exe est un programme qui compile les fichiers .xdc en fichier .xml. Un fichier. XDC est créé par le compilateur MSVC pour chaque fichier de code source lorsque le code source est compilé avec [/doc](doc-process-documentation-comments-c-cpp.md) et lorsque le fichier de code source contient des commentaires de documentation marqués avec des balises XML.

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Pour utiliser xdcmake.exe dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez le dossier **Propriétés de configuration**.

1. Cliquez sur la page de propriétés **Commentaires de document XML**.

> [!NOTE]
> Les options de xdcmake.exe au niveau de la ligne de commande diffèrent des options de xdcmake.exe quand celui-ci est utilisé dans l’environnement de développement (pages de propriétés). Pour plus d’informations sur l’utilisation de xdcmake.exe dans l’environnement de développement, consultez [Outil Générateur de documents XML, page de propriétés](xml-document-generator-tool-property-pages.md).

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
|/assembly:*nomfichier*|Vous permet de spécifier la valeur de la \<assembly> balise dans le fichier. Xml.  Par défaut, la valeur de la \<assembly> balise est identique à celle du fichier. Xml.|
|/nologo|Supprime le message de copyright.|
|/out:*nomfichier*|Vous permet de spécifier le nom du fichier .xml.  Par défaut, le nom du fichier .xml est le nom du premier fichier .xdc traité par xdcmake.exe.|

## <a name="remarks"></a>Notes

Visual Studio appelle xdcmake.exe automatiquement lors de la génération d’un projet. Vous pouvez également appeler xdcmake.exe à partir de la ligne de commande.

Consultez [Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md) pour plus d’informations sur l’ajout de commentaires de documentation aux fichiers de code source.

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
