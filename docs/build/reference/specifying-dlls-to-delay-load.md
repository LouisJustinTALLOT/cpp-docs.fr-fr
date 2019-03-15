---
title: Spécification de DLL dont le chargement doit être différé
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 2b6737abd76c03186881e83bbd2bf286be6ffe2f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813225"
---
# <a name="specifying-dlls-to-delay-load"></a>Spécification de DLL dont le chargement doit être différé

Vous pouvez spécifier qui chargent des DLL doit être différé avec la [/delayload](delayload-delay-load-import.md):`dllname` option de l’éditeur de liens. Si vous n'envisagez pas d'utiliser votre propre version d'une fonction d'assistance, vous devez également lier votre programme avec delayimp.lib (applications de bureau) ou dloadhelper.lib (pour les applications du Windows store).

Voici un exemple simple de chargement différé d'une DLL :

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

Générez la version DEBUG du projet. Parcourez le code pas à pas à l'aide du débogueur : vous noterez que user32.dll est chargée seulement quand vous effectuez l'appel à `MessageBox`.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](linker-support-for-delay-loaded-dlls.md)
