---
title: / Gd, / GR, GV, /Gz (convention d’appel) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3da8b4fcddbc384a785b27f0a7d706236a46ccf0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703770"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convention d’appel)
Ces options déterminent l’ordre dans la fonction qui les arguments sont placés sur la pile, si la fonction appelante ou la fonction appelée supprime les arguments de la pile à la fin de l’appel et la convention de décoration de nom que le compilateur utilise pour identifier fonctions individuelles.

## <a name="syntax"></a>Syntaxe

> **/Gd**<br/>
> **GR**<br/>
> **GV**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>Notes

**/Gd**, le paramètre par défaut, spécifie la [__cdecl](../../cpp/cdecl.md) convention d’appel pour toutes les fonctions membres C++ à l’exception de fonctions et les fonctions marquées [__stdcall](../../cpp/stdcall.md), [__ fastcall](../../cpp/fastcall.md), ou [__vectorcall](../../cpp/vectorcall.md).

**GR** Spécifie le `__fastcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, les fonctions nommées `main`et les fonctions marquées `__cdecl`, `__stdcall`, ou `__vectorcall`. Tous les `__fastcall` fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignoré par les compilateurs qui ciblent d’autres architectures.

**GZ** Spécifie le `__stdcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, les fonctions nommées `main`et les fonctions marquées `__cdecl`, `__fastcall`, ou `__vectorcall`. Tous les `__stdcall` fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignoré par les compilateurs qui ciblent d’autres architectures.

**GV** Spécifie le `__vectorcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, nommé principal les fonctions, les fonctions avec un `vararg` liste d’arguments variables ou des fonctions qui sont marquées avec un conflit lié à `__cdecl`, `__stdcall`, ou `__fastcall` attribut. Cette convention d’appel est disponible uniquement sur les architectures x86 et x64 qui prennent en charge SSE2 et versions ultérieures et est ignorée par les compilateurs qui ciblent l’architecture ARM.

Les fonctions qui acceptent un nombre variable d’arguments doivent être marquées `__cdecl`.

**/Gd**, **/GR**, **GV** et **GZ** ne sont pas compatibles avec [/CLR : safe](../../build/reference/clr-common-language-runtime-compilation.md) ou   **/CLR : pure**. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

> [!NOTE]
> Par défaut pour x86 processeurs, les fonctions membres C++ utilisent [__thiscall](../../cpp/thiscall.md).

Pour tous les processeurs, une fonction membre qui est marquée explicitement comme `__cdecl`, `__fastcall`, `__vectorcall`, ou `__stdcall` utilise la convention d’appel spécifiée si elle n’est pas ignoré sur cette architecture. Une fonction membre qui prend un nombre variable d’arguments toujours utilise le `__cdecl` convention d’appel.

Ces options du compilateur ont aucun effet sur la décoration de nom des méthodes et fonctions C++. À moins que déclaré en tant que `extern "C"`, méthodes et fonctions C++ utilisent un mécanisme de décoration de nom différent. Pour plus d’informations, consultez [noms décorés](../../build/reference/decorated-names.md).

Pour plus d’informations sur les conventions d’appel, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>particularités __cdecl

Sur x86 processeurs, tous les arguments de fonction sont passés sur la pile de droite à gauche. Sur ARM et x64 architectures, des arguments sont passés par Registre et les autres sont passés sur la pile de droite à gauche. La routine d’appel enlève les arguments de la pile.

Pour C, la `__cdecl` naming convention utilise le nom de fonction précédé d’un trait de soulignement ( `_` ) ; aucune conversion de casse n’est effectuée. À moins que déclaré en tant que `extern "C"`, les fonctions C++ utilisent un mécanisme de décoration de nom différent. Pour plus d’informations, consultez [noms décorés](../../build/reference/decorated-names.md).

## <a name="fastcall-specifics"></a>particularités de __fastcall

Certaines d’un `__fastcall` arguments de la fonction sont passés dans les registres (pour x86 processeurs, ECX et EDX), et le reste sont placé sur la pile de droite à gauche. La routine appelée dépile ces arguments à partir de la pile avant de retourner. En règle générale, **/GR** diminue le temps d’exécution.

> [!NOTE]
> Soyez prudent lorsque vous utilisez la `__fastcall` convention d’appel pour n’importe quelle fonction qui est écrit en langage assembleur inline. L’utilisation des registres pourrait être en conflit avec celle du compilateur.

Pour C, la `__fastcall` naming convention utilise le nom de fonction précédé par un arobase (`@`) suivie de la taille des arguments de la fonction en octets. Aucune conversion de casse n’est effectuée. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`@function_name@number`

Lorsque vous utilisez la `__fastcall` convention d’affectation de noms, utilisez les fichiers include standard. Sinon, vous obtiendrez des références externes non résolues.

## <a name="stdcall-specifics"></a>particularités de __stdcall

A `__stdcall` arguments de la fonction sont placés sur la pile de droite à gauche et la fonction appelée enlève ces arguments à partir de la pile avant de retourner.

Pour C, la `__stdcall` naming convention utilise le nom de fonction précédé d’un trait de soulignement ( `_` ) et suivie par un arobase (@) et la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`_functionname@number`

## <a name="vectorcall-specifics"></a>caractéristiques de __vectorcall

A `__vectorcall` arguments d’entier de la fonction sont passés par valeur, à l’aide de jusqu'à deux (sur x86) ou quatre (x64) entier inscrit et jusqu'à six XMM inscrit pour à virgule flottante et les valeurs de vecteur et le reste sont passés sur la pile de droite à gauche. La fonction appelée nettoie la pile avant de retourner. Vecteur et les valeurs de retournés à virgule flottante sont retournés dans XMM0.

Pour C, la `__vectorcall` convention d’affectation de noms utilise le nom de fonction suivi par deux signes arobase (@@) et la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **C/C++** > **avancé** page de propriétés.

1. Modifier la **Convention d’appel** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur](../../build/reference/compiler-options.md)
- [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
