---
title: /Gd, /Gr, /Gv, /Gz (Convention d'appel)
ms.date: 09/05/2018
f1_keywords:
- /gr
- /Gv
- /gz
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
ms.openlocfilehash: 72d65ce7471ed047ab8347a45c58a6b8a9f39a7a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450845"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convention d'appel)

Ces options déterminent l’ordre dans lequel les arguments de fonction sont envoyés dans la pile, si la fonction de l’appelant ou la fonction appelée supprime les arguments de la pile à la fin de l’appel, ainsi que la convention de décoration de nom que le compilateur utilise pour identifier des fonctions individuelles.

## <a name="syntax"></a>Syntaxe

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>Notes

**/Gd**, le paramètre par défaut, spécifie la convention d’appel [__cdecl](../../cpp/cdecl.md) pour toutes les fonctions hormis les fonctions membres C++ et les fonctions marquées [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md) ou [__vectorcall](../../cpp/vectorcall.md).

**/Gr** spécifie la convention d’appel `__fastcall` pour toutes les fonctions hormis les fonctions membres C++, les fonctions nommées `main` et les fonctions marquées `__cdecl`, `__stdcall` ou `__vectorcall`. Toutes les fonctions `__fastcall` doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**/Gz** spécifie la convention d’appel `__stdcall` pour toutes les fonctions hormis les fonctions membres C++, les fonctions nommées `main` et les fonctions marquées `__cdecl`, `__fastcall` ou `__vectorcall`. Toutes les fonctions `__stdcall` doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**GV** Spécifie le `__vectorcall` convention d’appel pour toutes les fonctions hormis C++ fonctions membres, des fonctions nommées `main`, fonctions avec un `vararg` liste d’arguments variables ou fonctions qui sont marquées avec un conflit lié à `__cdecl`, `__stdcall`, ou `__fastcall` attribut. Cette convention d’appel est disponible uniquement sur les architectures x86 et x64 qui prennent en charge/arch:SSE2 et ultérieur, et est ignorée par les compilateurs qui ciblent l’architecture ARM.

Les fonctions qui prennent un nombre variable d’arguments doivent être marquées `__cdecl`.

**/Gd**, **/Gr**, **/Gv** et **/Gz** ne sont pas compatibles avec [/clr:safe](clr-common-language-runtime-compilation.md) ni **/clr:pure**. Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur.

> [!NOTE]
> Par défaut pour les processeurs x86, les fonctions membres C++ utilisent [__thiscall](../../cpp/thiscall.md).

Pour tous les processeurs, une fonction membre qui est marquée explicitement comme `__cdecl`, `__fastcall`, `__vectorcall`, ou `__stdcall` utilise la convention d’appel spécifiée si elle n’est pas ignorée sur cette architecture. Une fonction membre qui accepte un nombre variable d’arguments utilise toujours la convention d’appel `__cdecl`.

Ces options du compilateur n’ont aucun effet sur la décoration de nom des fonctions et méthodes C++. À moins d’être déclarées comme `extern "C"`, les fonctions et méthodes C++ utilisent un mécanisme de décoration de nom différent. Pour plus d’informations, consultez [Noms décorés](decorated-names.md).

Pour plus d’informations sur les conventions d’appel, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>Spécificités de __cdecl

Sur les processeurs x86, tous les arguments de fonction sont passés sur la pile de droite à gauche. Sur les architectures ARM et x64, certains arguments sont passés par le registre et les autres sont passés sur la pile de droite à gauche. La routine d’appel enlève les arguments de la pile.

Pour C, la convention de nommage `__cdecl` utilise le nom de fonction précédé par un trait de soulignement ( `_` ) ; aucune conversion de casse n’est effectuée. À moins d’être déclarées comme `extern "C"`, les fonctions C++ utilisent un autre mécanisme de décoration de nom. Pour plus d’informations, consultez [Noms décorés](decorated-names.md).

## <a name="fastcall-specifics"></a>Spécificités de __fastcall

Certains des arguments d’une fonction `__fastcall` sont passés dans les registres (pour les processeurs x86, ECX et EDX), et les autres sont envoyés dans la pile de droite à gauche. La routine appelée enlève ces arguments de la pile avant d’être retournée. En règle générale, **/Gr** diminue la durée d’exécution.

> [!NOTE]
> Soyez prudent lorsque vous utilisez la convention d’appel `__fastcall` pour n’importe quelle fonction qui est écrite en langage assembleur inline. L’utilisation des registres peut entrer en conflit avec celle du compilateur.

Pour C, la convention de nommage `__fastcall` utilise le nom de fonction précédé par un arobase ( **\@** ) suivi de la taille des arguments de la fonction en octets. Aucune conversion de casse n’est effectuée. Le compilateur utilise le modèle suivant pour la convention de nommage :

`@function_name@number`

Lorsque vous utilisez la convention de nommage `__fastcall`, utilisez les fichiers include standard. Sinon, vous obtiendrez des références externes non résolues.

## <a name="stdcall-specifics"></a>Spécificités de __stdcall

Les arguments d’une fonction `__stdcall` sont envoyés dans la pile de droite à gauche, et la fonction appelée enlève ces arguments de la pile avant d’être retournée.

Pour C, la convention de nommage `__stdcall` utilise le nom de fonction précédé par un trait de soulignement ( **\_** ) et suivi d’un arobase ( **\@** ) et de la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise le modèle suivant pour la convention de nommage :

`_functionname@number`

## <a name="vectorcall-specifics"></a>Spécificités de __vectorcall

Les arguments entiers d’une fonction `__vectorcall` sont passés par valeur, en utilisant jusqu’à deux (sur x86) ou quatre (sur x64) registres d’entiers, et jusqu’à six registres XMM pour les valeurs à virgule flottante et vectorielles, et les autres sont passés sur la pile de droite à gauche. La fonction appelée nettoie la pile avant d’être retournée. Les valeurs de retour à virgule flottante et vectorielles sont retournées dans XMM0.

Pour C, la convention de nommage `__vectorcall` utilise le nom de fonction suivi de deux arobases ( **\@\@** ) et la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise le modèle suivant pour la convention de nommage :

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **C/C++**  > **Avancé**.

1. Modifiez la propriété **Convention d’appel**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur MSVC](compiler-options.md)
- [Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
