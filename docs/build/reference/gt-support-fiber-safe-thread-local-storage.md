---
title: -GT (prise en charge des fibres sécurisées Thread-Local Storage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs:
- C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eeec9ddce36777fc6fcb15b30a864f1c04a7b09b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700834"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Prendre en charge le stockage local des threads avec fibres sécurisées)

Prend en charge de la sécurité des fibres pour les données allouées à l’aide du stockage local des threads statique, autrement dit, les données allouées avec `__declspec(thread)`.

## <a name="syntax"></a>Syntaxe

```
/GT
```

## <a name="remarks"></a>Notes

Données déclarées avec `__declspec(thread)` est référencé via une baie de stockage local des threads (TLS). Le tableau TLS est un tableau d’adresses que le système gère pour chaque thread. Chaque adresse de ce tableau indique l’emplacement de données de stockage local des threads.

Une fibre est un objet léger qui se compose d’une pile et un contexte de Registre et peut être planifié sur différents threads. Une fibre peut être exécutée sur n’importe quel thread. Comme une fibre peut être transférée et redémarrée ultérieurement sur un thread différent, l’adresse du tableau TLS ne doit pas être mis en cache ou optimisée en tant qu’une sous-expression commune dans un appel de fonction (voir la [/Og (optimisations globales)](../../build/reference/og-global-optimizations.md) option pour (détails). **/GT** empêche ces optimisations.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **optimisation** page de propriétés.

1. Modifier le **activer les optimisations à fibres sécurisées** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)