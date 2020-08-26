---
title: Valeur de retour de cl.exe
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 06e0993f6a96117ab73f22e73857843dfcc334a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836723"
---
# <a name="return-value-of-clexe"></a>Valeur de retour de cl.exe

cl.exe retourne zéro en cas de réussite (aucune erreur) et une valeur différente de zéro dans les autres cas.

La valeur de retour de cl.exe peut être utile si vous compilez à partir d'un fichier script, powershell, .cmd ou .bat. Il est recommandé de capturer la sortie du compilateur afin de pouvoir résoudre les erreurs ou avertissements éventuels.

Il y a trop de codes de sortie d'erreur possibles pour que cl.exe puisse tous les répertorier. Vous pouvez rechercher un code d’erreur dans les fichiers winerror. h ou Ntstatus. h inclus dans le kit de développement logiciel (SDK) Windows dans le répertoire% ProgramFiles (x86)% \ Windows kits \\ <em>version</em>\Include\shared\ Les codes d'erreur retournés au format décimal doivent être convertis au format hexadécimal pour la recherche. Par exemple, le code d'erreur -1073741620 converti au format hexadécimal correspond à 0xC00000CC. Cette erreur se trouve dans ntstatus.h, où le message correspondant est « La ressource partagée spécifiée sur le serveur distant est introuvable. » Pour obtenir la liste téléchargeable des codes d’erreur Windows, consultez [&#91;MS-ERREF&#93; : codes d’erreur Windows](/openspecs/windows_protocols/MS-ERREF).

Vous pouvez également utiliser l'utilitaire de recherche d'erreurs dans Visual Studio pour connaître la signification d'un message d'erreur du compilateur. Dans une interface de commande Visual Studio, entrez **errlook.exe** pour démarrer l’utilitaire. ou, dans l’IDE de Visual Studio, dans la barre de menus, choisissez **Outils**, **recherche d’erreurs**. Entrez la valeur d'erreur pour rechercher le texte descriptif associé à l'erreur. Pour plus d’informations, consultez [référence d’ERRLOOK](errlook-reference.md).

## <a name="remarks"></a>Notes

Vous trouverez ci-dessous un exemple de fichier .bat qui utilise la valeur de retour de cl.exe.

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
