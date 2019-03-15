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
ms.openlocfilehash: 7c4f7e6edb020f5c8d2abf80f14df33e18a915c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817463"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convention d'appel)

Ces options déterminent l’ordre dans lesquels fonction arguments sont transmis dans la pile, si la fonction appelante ou la fonction appelée supprime les arguments de la pile à la fin de l’appel et la convention de décoration de nom que le compilateur utilise pour identifier fonctions individuelles.

## <a name="syntax"></a>Syntaxe

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>Notes

**/Gd**, le paramètre par défaut, spécifie la [__cdecl](../../cpp/cdecl.md) convention d’appel pour toutes les fonctions membres C++ à l’exception de fonctions et des fonctions qui sont marquées [__stdcall](../../cpp/stdcall.md), [__ fastcall](../../cpp/fastcall.md), ou [__vectorcall](../../cpp/vectorcall.md).

**/ GR** Spécifie le `__fastcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, fonctions nommées `main`et les fonctions qui sont marquées `__cdecl`, `__stdcall`, ou `__vectorcall`. Tous les `__fastcall` fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**/GZ** Spécifie le `__stdcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, fonctions nommées `main`et les fonctions qui sont marquées `__cdecl`, `__fastcall`, ou `__vectorcall`. Tous les `__stdcall` fonctions doivent avoir des prototypes. Cette convention d’appel est uniquement disponible dans les compilateurs qui ciblent x86 et est ignorée par les compilateurs qui ciblent d’autres architectures.

**GV** Spécifie le `__vectorcall` convention d’appel pour toutes les fonctions hormis les fonctions membres C++, fonctions nommées principal, fonctions avec un `vararg` liste d’arguments variables ou fonctions qui sont marquées avec un conflit lié à `__cdecl`, `__stdcall`, ou `__fastcall` attribut. Cette convention d’appel est disponible uniquement sur les architectures x86 et x64 qui prennent en charge/arch : SSE2 et versions ultérieures et est ignorée par les compilateurs qui ciblent l’architecture ARM.

Les fonctions qui acceptent un nombre variable d’arguments doivent être marquées `__cdecl`.

**/Gd**, **/GR**, **GV** et **/Gz** ne sont pas compatibles avec [/CLR : safe](clr-common-language-runtime-compilation.md) ou   **/CLR : pure**. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

> [!NOTE]
> Par défaut pour x86 processeurs, fonctions membres C++ utilisent [__thiscall](../../cpp/thiscall.md).

Pour tous les processeurs, une fonction membre qui est marquée explicitement comme `__cdecl`, `__fastcall`, `__vectorcall`, ou `__stdcall` utilise la convention d’appel spécifiée si elle n’est pas ignorée dans cette architecture. Une fonction membre qui accepte un nombre variable d’arguments toujours utilise le `__cdecl` convention d’appel.

Ces options du compilateur n’ont aucun effet sur la décoration de noms des méthodes et fonctions C++. Sauf si déclarée comme `extern "C"`, fonctions et méthodes C++ utilisent un mécanisme de décoration de noms différent. Pour plus d’informations, consultez [noms décorés](decorated-names.md).

Pour plus d’informations sur les conventions d’appel, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>particularités __cdecl

Sur x86 processeurs, tous les arguments de fonction sont passés sur la pile de droite à gauche. Sur ARM et x64 architectures, certains arguments sont passés par le Registre et les autres sont passés sur la pile de droite à gauche. La routine d’appel enlève les arguments de la pile.

Pour C, la `__cdecl` naming convention utilise le nom de fonction précédé par un trait de soulignement ( `_` ) ; aucune conversion de casse n’est effectuée. Sauf si déclarée comme `extern "C"`, les fonctions C++ utilisent un mécanisme de décoration de nom différent. Pour plus d’informations, consultez [noms décorés](decorated-names.md).

## <a name="fastcall-specifics"></a>particularités de __fastcall

Certaines d’un `__fastcall` arguments de fonction sont passés dans les registres (pour x86 processeurs, ECX et EDX), et le reste sont envoyées dans la pile de droite à gauche. La routine appelée dépile ces arguments de la pile avant son retour. En règle générale, **/GR** diminue les temps d’exécution.

> [!NOTE]
> Soyez prudent lorsque vous utilisez le `__fastcall` convention d’appel pour n’importe quelle fonction qui est écrit en langage assembleur inline. L’utilisation des registres peut entrer en conflit avec celle du compilateur.

Pour C, la `__fastcall` naming convention utilise le nom de fonction précédé par un arobase (**\@**) suivie de la taille des arguments de la fonction en octets. Aucune conversion de casse n’est effectuée. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`@function_name@number`

Lorsque vous utilisez le `__fastcall` convention d’affectation de noms, utilisez les fichiers include standard. Sinon, vous obtiendrez des références externes non résolues.

## <a name="stdcall-specifics"></a>particularités de __stdcall

Un `__stdcall` arguments de fonction sont poussés sur la pile de droite à gauche, et la routine appelée dépile ces arguments de la pile avant son retour.

Pour C, la `__stdcall` naming convention utilise le nom de fonction précédé par un trait de soulignement (**\_**) et suivie par un arobase (**\@**) et la taille de la fonction arguments en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`_functionname@number`

## <a name="vectorcall-specifics"></a>caractéristiques spécifiques de __vectorcall

Un `__vectorcall` arguments de type entier de la fonction sont passés par valeur, en utilisant jusqu'à deux (sur x86) ou quatre (sur x64) entier inscrit et jusqu'à six registres XMM pour à virgule flottante et les valeurs de vecteur et le reste sont passés sur la pile de droite à gauche. La fonction appelée nettoie la pile avant son retour. Vecteur et les valeurs de retournés à virgule flottante sont retournés dans XMM0.

Pour C, la `__vectorcall` convention d’affectation de noms utilise le nom de fonction suivi par deux signes arobase (**\@\@**) et la taille des arguments de la fonction en octets. Aucune conversion de casse n'a lieu. Le compilateur utilise ce modèle pour la convention d’affectation de noms :

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** > **avancé** page de propriétés.

1. Modifier le **Convention d’appel** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur MSVC](compiler-options.md)
- [Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
