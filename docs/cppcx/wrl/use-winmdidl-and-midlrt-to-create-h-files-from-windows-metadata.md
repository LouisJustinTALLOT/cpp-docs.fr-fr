---
title: 'Procédure : Utiliser winmdidl.exe et midlrt.exe pour créer des fichiers .h à partir de métadonnées windows'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: b9016f05b82e3eb04474d370bd069e8008de5278
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784459"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Procédure : Utiliser winmdidl.exe et midlrt.exe pour créer des fichiers .h à partir de métadonnées windows

Winmdidl.exe et midlrt.exe permettent l'interaction de niveau COM entre le code C++ natif et les composants Windows Runtime. Winmdidl.exe prend comme entrée un fichier .winmd qui contient des métadonnées pour un composant Windows Runtime et génère un fichier IDL. Midlrt.exe convertit ce fichier IDL en fichiers d'en-tête que le code C++ peut utiliser. Les deux outils sont exécutés sur la ligne de commande.

Vous utilisez ces outils dans deux scénarios principaux :

- Création de fichiers d'en-tête et IDL personnalisés pour qu'une application C++ écrite à l'aide de la bibliothèque de modèles Windows Runtime (WRL) puisse utiliser un composant Windows Runtime personnalisé

- Génération de fichiers de proxy et stub pour les types d'événements définis par l'utilisateur dans un composant Windows Runtime Pour plus d’informations, consultez [événements personnalisés et accesseurs d’événement dans les composants Windows Runtime](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Ces outils ne sont nécessaires que pour analyser les fichiers .winmd personnalisés. Les fichiers .idl et .h pour les composants de système d'exploitation Windows sont automatiquement générés. Par défaut dans Windows 8.1, ils se trouvent dans \Program fichiers (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Emplacement des outils

Par défaut dans [Windows 8.1, winmdidl.exe et midlrt.exe se trouvent dans C:\Program Files (x86) \Windows Kits\8.1\\. Des versions des outils sont également disponibles dans les dossiers \bin\x86\ et \bin\x64\.

## <a name="winmdidl-command-line-arguments"></a>Arguments de ligne de commande Winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Empêche l'affichage dans la console du message de copyright et du numéro de version winmdidl. 

**/suppressversioncheck**<br/>
Non utilisé.

**/time**<br/>
Affiche la durée totale d'exécution dans la sortie de la console.

**/outdir:**<em>dir</em><br/>
Spécifie un répertoire de sortie. Si le chemin d’accès contient des espaces, placez-le entre guillemets. Le répertoire de sortie par défaut est  *\<lecteur >*: \Users\\*\<nom d’utilisateur >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft Visual Studio 12.0\\.

**/ bannière :**<em>fichier</em><br/>
Spécifie un fichier qui contient le texte personnalisé à faire figurer avant le message de copyright et le numéro de version winmdidl par défaut au début du fichier .idl généré. Si le chemin d’accès contient des espaces, placez-le entre guillemets.

**/utf8**<br/>
Le format du fichier sera UTF-8.

*Winmdfile*<br/>
Nom du fichier .winmd à analyser. Si le chemin d’accès contient des espaces, placez-le entre guillemets.

## <a name="midlrt-command-line-arguments"></a>Arguments de ligne de commande Midlrt

Consultez [composants MIDLRT et Windows Runtime](/windows/desktop/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Exemples

L'exemple suivant montre une commande winmdidl à une invite de commandes Visual Studio x86. Elle spécifie un répertoire de sortie et un fichier qui contient le texte de bannière spécial à ajouter au fichier .idl généré.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

L'exemple suivant illustre l'affichage de la console à partir de winmdidl qui indique que l'opération a réussi.

**Generating c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

Ensuite, midlrt est exécuté sur le fichier IDL généré. Notez que le **metadata_dir** argument est spécifié après le nom du fichier .idl. Le chemin d'accès de \WinMetadata\ est obligatoire ; il s'agit de l'emplacement de windows.winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Notes

Le fichier de sortie d'une opération winmdidl a le même nom que le fichier d'entrée, mais porte l'extension de nom de fichier .idl.

Si vous développez un composant Windows Runtime qui est accessible à partir de la bibliothèque WRL, vous pouvez spécifier que winmdidl.exe et midlrt.exe s'exécutent en guise d'étapes post-builds pour que les fichiers .idl et .h soient générés sur chaque build. Pour obtenir un exemple, consultez [déclenchement d’événements dans les composants Windows Runtime](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).