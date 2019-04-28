---
title: /DEBUGTYPE (options d'informations de débogage)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 00e3cb61f8ec9aa707bb72aa9ff05a64f98d4e47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272293"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (options d'informations de débogage)

L'option /DEBUGTYPE spécifie les types d'informations de débogage générées par l'option /DEBUG.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>Arguments

**CV**<br/>
Indique à l'éditeur de liens d'émettre des informations de débogage pour les symboles, les numéros de ligne et d'autres informations de compilation d'objet dans le fichier PDB. Par défaut, cette option est activée lorsque **/DEBUG** est spécifié et **/DEBUGTYPE** n’est pas spécifié.

**PDATA**<br/>
Indique à l'éditeur de liens d'ajouter des entrées .pdata et .xdata aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsqu’à la fois le **/DEBUG** et **/DRIVER** options sont spécifiées. Si **/DEBUGTYPE:PDATA** est spécifié par lui-même, l’éditeur de liens inclut automatiquement des symboles de débogage dans le fichier PDB. Si **/DEBUGTYPE:PDATA, correction** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.

**CORRECTION**<br/>
Indique à l'éditeur de liens d'ajouter des entrées de table de réadressage aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsqu’à la fois le **/DEBUG** et **/PROFILE** options sont spécifiées. Si **/DEBUGTYPE:FIXUP** ou **/DEBUGTYPE:FIXUP, PDATA** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.

Arguments à **/DEBUGTYPE** peuvent être combinées dans n’importe quel ordre, en les séparant par une virgule. Le **/DEBUGTYPE** option et ses arguments ne sont pas sensible à la casse.

## <a name="remarks"></a>Notes

Utilisez le **/DEBUGTYPE** option pour spécifier l’inclusion de réadressage des données ou .pdata et .xdata en-tête informations sur la table dans le flux de débogage. Par conséquent, l'éditeur de liens inclut des informations concernant le code en mode utilisateur qui est visible dans un débogueur du noyau lors de la séparation de code en mode noyau. Pour rendre les symboles de débogage disponibles quand **correction** est spécifié, incluez le **CV** argument.

Pour déboguer le code en mode utilisateur, qui est généralement utilisé pour les applications, le **/DEBUGTYPE** option n’est pas nécessaire. Par défaut, les commutateurs de compilation qui spécifient le débogage de sortie ([/Z7, / Zi, / Zi](z7-zi-zi-debug-information-format.md)) émettent toutes les informations requises par Visual Studio du débogueur. Utilisez **/DEBUGTYPE:PDATA** ou **/DEBUGTYPE : CV, PDATA, correction** pour déboguer le code qui combine les composants en mode utilisateur et en mode noyau, par exemple une application de configuration pour un pilote de périphérique. Pour plus d’informations sur les débogueurs en mode noyau, consultez [débogage outils pour Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>Voir aussi

[/DEBUG (Générer les informations de débogage)](debug-generate-debug-info.md)<br/>
[/DRIVER (Pilote Windows NT en mode noyau)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (Profileur des outils d’analyse des performances)](profile-performance-tools-profiler.md)<br/>
[Outils de débogage pour Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)
