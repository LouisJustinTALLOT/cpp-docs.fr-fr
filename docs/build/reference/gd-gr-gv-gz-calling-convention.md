---
description: En savoir plus sur:/GD,/GR,/GV,/gz (Convention d’appel)
title: /Gd, /Gr, /Gv, /Gz (Convention d'appel)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
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
ms.openlocfilehash: dd343466efd0b3b0d93fc783cd7e4305c2295ef3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200323"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convention d'appel)

Ces options déterminent l’ordre dans lequel les arguments de fonction sont envoyés dans la pile, si la fonction de l’appelant ou la fonction appelée supprime les arguments de la pile à la fin de l’appel, ainsi que la convention de décoration de nom que le compilateur utilise pour identifier des fonctions individuelles.

## <a name="syntax"></a>Syntaxe

> **`/Gd`**\
> **`/Gr`**\
> **`/Gv`**\
> **`/Gz`**

## <a name="remarks"></a>Notes

**`/Gd`**, le paramètre par défaut, spécifie la Convention d’appel [__cdecl](../../cpp/cdecl.md) pour toutes les fonctions, à l’exception des fonctions membres C++ et des fonctions marquées [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)ou [__vectorcall](../../cpp/vectorcall.md).

**`/Gr`** spécifie la **`__fastcall`** Convention d’appel pour toutes les fonctions à l’exception des fonctions membres C++, des fonctions nommées `main` et des fonctions marquées **`__cdecl`** , **`__stdcall`** ou **`__vectorcall`** . Toutes les **`__fastcall`** fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**`/Gz`** spécifie la **`__stdcall`** Convention d’appel pour toutes les fonctions à l’exception des fonctions membres C++, des fonctions nommées `main` et des fonctions marquées **`__cdecl`** , **`__fastcall`** ou **`__vectorcall`** . Toutes les **`__stdcall`** fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**`/Gv`** spécifie la **`__vectorcall`** Convention d’appel pour toutes les fonctions à l’exception des fonctions membres C++, des fonctions nommées `main` , des fonctions avec une `vararg` liste d’arguments de variable ou des fonctions marquées avec un **`__cdecl`** attribut, ou en conflit **`__stdcall`** **`__fastcall`** . Cette convention d’appel est disponible uniquement sur les architectures x86 et x64 qui prennent en charge/arch:SSE2 et ultérieur, et est ignorée par les compilateurs qui ciblent l’architecture ARM.

Les fonctions qui acceptent un nombre variable d’arguments doivent être marquées **`__cdecl`** .

**`/Gd`**, **`/Gr`** **`/Gv`** et **`/Gz`** ne sont pas compatibles avec [`/clr:safe`](clr-common-language-runtime-compilation.md) ou **/clr : pure**. Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur.

> [!NOTE]
> Par défaut pour les processeurs x86, les fonctions membres C++ utilisent [`__thiscall`](../../cpp/thiscall.md) .

Pour tous les processeurs, une fonction membre qui est marquée explicitement comme **`__cdecl`** , **`__fastcall`** , **`__vectorcall`** ou **`__stdcall`** utilise la Convention d’appel spécifiée si elle n’est pas ignorée sur cette architecture. Une fonction membre qui accepte un nombre variable d’arguments utilise toujours la **`__cdecl`** Convention d’appel.

Ces options du compilateur n’ont aucun effet sur la décoration de nom des fonctions et méthodes C++. À moins d’être déclarées comme `extern "C"`, les fonctions et méthodes C++ utilisent un mécanisme de décoration de nom différent. Pour plus d’informations, consultez [Noms décorés](decorated-names.md).

Pour plus d’informations sur les conventions d’appel, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>Spécificités de __cdecl

Sur les processeurs x86, tous les arguments de fonction sont passés sur la pile de droite à gauche. Sur les architectures ARM et x64, certains arguments sont passés par le registre et les autres sont passés sur la pile de droite à gauche. La routine d’appel enlève les arguments de la pile.

Pour C, la **`__cdecl`** Convention d’affectation de noms utilise le nom de fonction précédé d’un trait de soulignement ( `_` ); aucune conversion de casse n’est effectuée. À moins d’être déclarées comme `extern "C"`, les fonctions C++ utilisent un autre mécanisme de décoration de nom. Pour plus d’informations, consultez [Noms décorés](decorated-names.md).

## <a name="__fastcall-specifics"></a>Spécificités de __fastcall

Certains des arguments d’une **`__fastcall`** fonction sont passés dans les registres (pour les processeurs x86, ecx et EDX), et les autres font l’objet d’un push sur la pile de droite à gauche. La routine appelée enlève ces arguments de la pile avant d’être retournée. En règle générale, **/Gr** diminue la durée d’exécution.

> [!NOTE]
> Soyez prudent lorsque vous utilisez la **`__fastcall`** Convention d’appel pour toute fonction écrite en langage assembleur inline. L’utilisation des registres peut entrer en conflit avec celle du compilateur.

Pour C, la **`__fastcall`** Convention d’affectation de noms utilise le nom de fonction précédé d’un arobase ( **\@** ) suivi de la taille des arguments de la fonction en octets. Aucune conversion de casse n’est effectuée. Le compilateur utilise le modèle suivant pour la convention de nommage :

`@function_name@number`

Lorsque vous utilisez la **`__fastcall`** Convention d’affectation de noms, utilisez les fichiers Include standard. Sinon, vous obtiendrez des références externes non résolues.

## <a name="__stdcall-specifics"></a>Spécificités de __stdcall

Les **`__stdcall`** arguments d’une fonction font l’objet d’un push sur la pile de droite à gauche, et la fonction appelée dépile ces arguments à partir de la pile avant qu’elle ne soit retournée.

Pour C, la **`__stdcall`** Convention d’affectation de noms utilise le nom de fonction précédé d’un trait de soulignement ( **\_** ) et suivi d’un arobase ( **\@** ) et de la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise le modèle suivant pour la convention de nommage :

`_functionname@number`

## <a name="__vectorcall-specifics"></a>Spécificités de __vectorcall

Les **`__vectorcall`** arguments entiers d’une fonction sont passés par valeur, en utilisant jusqu’à deux (sur x86) ou quatre (sur x64) des registres d’entiers, et jusqu’à six registres XMM pour les valeurs à virgule flottante et des vecteurs, et le reste est passé sur la pile de droite à gauche. La fonction appelée nettoie la pile avant d’être retournée. Les valeurs de retour à virgule flottante et vectorielles sont retournées dans XMM0.

Pour C, la **`__vectorcall`** Convention d’affectation de noms utilise le nom de la fonction suivi de deux signes arobase ( **\@\@** ) et de la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise le modèle suivant pour la convention de nommage :

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé **C/C++**  >   .

1. Modifiez la propriété **Convention d’appel**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur MSVC](compiler-options.md)
- [Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
