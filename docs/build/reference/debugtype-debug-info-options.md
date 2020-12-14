---
description: En savoir plus sur:/DEBUGTYPE (options des informations de débogage)
title: /DEBUGTYPE (options d'informations de débogage)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 858d5ed8eb449931229700a10b755dd61ef371cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201727"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (options d'informations de débogage)

L'option /DEBUGTYPE spécifie les types d'informations de débogage générées par l'option /DEBUG.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>Arguments

**CV**<br/>
Indique à l'éditeur de liens d'émettre des informations de débogage pour les symboles, les numéros de ligne et d'autres informations de compilation d'objet dans le fichier PDB. Par défaut, cette option est activée quand **/Debug** est spécifié et **/DebugType** n’est pas spécifié.

**PDATA**<br/>
Indique à l'éditeur de liens d'ajouter des entrées .pdata et .xdata aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsque les options **/Debug** et **/Driver** sont spécifiées. Si **/DebugType : pData** est spécifié par lui-même, l’éditeur de liens comprend automatiquement les symboles de débogage dans le fichier PDB. Si **/DebugType : pData, Fixup** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.

**FIXUP**<br/>
Indique à l'éditeur de liens d'ajouter des entrées de table de réadressage aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsque les options **/Debug** et **/Profile** sont spécifiées. Si **/DebugType : Fixup** ou **/DebugType : Fixup, pData** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.

Les arguments de **/DebugType** peuvent être combinés dans n’importe quel ordre en les séparant par une virgule. L’option **/DebugType** et ses arguments ne respectent pas la casse.

## <a name="remarks"></a>Notes

Utilisez l’option **/DebugType** pour spécifier l’inclusion de données de table de réadressage ou d’informations d’en-tête. pdata et. XData dans le flux de débogage. Par conséquent, l'éditeur de liens inclut des informations concernant le code en mode utilisateur qui est visible dans un débogueur du noyau lors de la séparation de code en mode noyau. Pour rendre les symboles de débogage disponibles lorsque la **Correction** est spécifiée, incluez l’argument **CV** .

Pour déboguer du code en mode utilisateur, ce qui est courant pour les applications, l’option **/DebugType** n’est pas nécessaire. Par défaut, le compilateur commutateurs qui spécifient la sortie de débogage ([/Z7,/Zi,/Zi](z7-zi-zi-debug-information-format.md)) émettent toutes les informations requises par le débogueur Visual Studio. Utilisez **/DebugType : pData** ou **/DebugType : CV, pData, correction** pour déboguer le code qui combine les composants en mode utilisateur et en mode noyau, comme une application de configuration pour un pilote de périphérique. Pour plus d’informations sur les débogueurs en mode noyau, consultez [outils de débogage pour Windows (WinDbg, KD, CDB, ntsd)](/windows-hardware/drivers/debugger/index) .

## <a name="see-also"></a>Voir aussi

[/DEBUG (générer les informations de débogage)](debug-generate-debug-info.md)<br/>
[/DRIVER (pilote Windows NT en mode noyau)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (profileur des outils d’exécution des performances)](profile-performance-tools-profiler.md)<br/>
[Outils de débogage pour Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)
