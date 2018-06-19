---
title: -noyau (créer Kernel Mode binaire) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbae275e751287464e4bf1637ee21aff77fb697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379599"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Créer un fichier binaire pour le mode noyau)
Crée un fichier binaire qui peut être exécuté dans le noyau Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>Arguments  
 **/kernel**  
 Le code dans le projet actuel est compilé et lié à l’aide d’un ensemble de règles de langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.  
  
 **/Kernel-**  
 Le code dans le projet actuel est compilé et lié sans utiliser les règles de langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.  
  
## <a name="remarks"></a>Notes  
 Il existe aucune `#pragma` équivalente pour contrôler cette option.  
  
 En spécifiant le **/kernel** option indique au compilateur et l’éditeur de liens pour déterminer les fonctionnalités de langage sont autorisées en mode noyau et s’assurer que vous avez suffisamment puissance expressive afin d’éviter l’instabilité du runtime qui est unique en mode noyau C++. Cela est accompli en interdisant l’utilisation de fonctionnalités du langage C++ qui sont en mode noyau interruption de service et en fournissant des avertissements pour les fonctionnalités du langage C++ qui sont potentiellement dangereuses, mais ne peut pas être désactivées.  
  
 Le **/kernel** option s’applique aux phases le compilateur et l’éditeur de liens d’une build et est définie au niveau du projet. Passez le **/kernel** commutateur pour indiquer au compilateur que la sortie binaire, après avoir lié, doit être chargée dans le noyau Windows. Le compilateur restreindra la gamme des fonctionnalités du langage C++ à un sous-ensemble qui est compatible avec le noyau.  
  
 Le tableau suivant répertorie les modifications de comportement du compilateur lorsque **/kernel** est spécifié.  
  
|Type de comportement|**/Kernel** comportement|  
|-------------------|---------------------------|  
|Gestion d'exceptions C++|Désactivé. Toutes les instances de la `throw` et `try` mots clés émettre une erreur du compilateur (à l’exception de la spécification d’exception `throw()`). Ne **/EH** options sont compatibles avec **/kernel**, à l’exception de **/EH-**.|  
|RTTI|Désactivé. Toutes les instances de la `dynamic_cast` et `typeid` mots clés émettre une erreur du compilateur, sauf si `dynamic_cast` est utilisée de manière statique.|  
|`new` et `delete`|Vous devez définir explicitement la `new()` ou `delete()` opérateur ; le compilateur ni le runtime fournit une définition default.|  
  
 Custom conventions d’appel, le [/GS](../../build/reference/gs-buffer-security-check.md) option de génération et toutes les optimisations sont autorisés lorsque vous utilisez la **/kernel** option. La fonctionnalité inline n’est en grande partie pas affectée par **/kernel**, avec la même sémantique que honorée par le compilateur. Si vous souhaitez vous assurer que le `__forceinline` qualificateur d’incorporation (inlining) est respecté, vous devez vous assurer qu’avertissement [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) est activée afin que vous sachiez quand un particulier `__forceinline` fonction n’est pas inline.  
  
 Lorsque le compilateur est passé le **/kernel** commutateur, il prédéfinit préprocesseur ou macro nommé `_KERNEL_MODE` et a la valeur **1**. Vous pouvez utiliser cela pour effectuer une compilation conditionnelle selon que l’environnement d’exécution est en mode utilisateur ou en mode noyau de code. Par exemple, le code suivant spécifie que la classe doit être dans un segment de mémoire non paginable lorsqu’il est compilé pour l’exécution en mode noyau.  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
   // ...
};  
```  
  
 Certaines combinaisons suivantes de l’architecture cible et le **/arch** option génère une erreur lorsqu’elles sont utilisées avec **/kernel**:  
  
-   **/ arch : {SSE&#124;SSE2&#124;AVX}** ne sont pas pris en charge sur x86. Uniquement **/arch:IA32** est pris en charge avec **/kernel** sur x86.  
  
-   **/ arch : AVX** n’est pas pris en charge avec **/kernel** sur x64.  
  
 Génération avec **/kernel** passe également **/kernel** à l’éditeur de liens. Voici comment cela affecte le comportement de l’éditeur de liens :  
  
-   Liaison incrémentielle est désactivée. Si vous ajoutez **/ incremental** à la ligne de commande, l’éditeur de liens émet cette erreur irrécupérable :  
  
     **LIEN : erreur irrécupérable des LNK1295 : '/ INCREMENTAL' non compatible avec ' / noyau ' spécification ; lier sans '/ INCRÉMENTIELLES**  
  
-   L’éditeur de liens inspecte chaque fichier objet (ou n’importe quel membre archive inclus à partir de bibliothèques statiques) pour voir si il peut avoir été compilé à l’aide de la **/kernel** option mais n’était pas. Si toutes les instances répondent à ce critère, l’éditeur de liens lie toujours avec succès mais peut émettre un avertissement, comme indiqué dans le tableau suivant.  
  
    ||**/Kernel** obj|**/Kernel-** obj, MASM obj, ou cvtresed|Un mélange de **/kernel** et **/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**lien /kernel**|Oui|Oui|Oui avec avertissement LNK4257|  
    |**Lien**|Oui|Oui|Oui|  
  
     **Objet de liaison de LNK4257 ne pas compilé avec /KERNEL ; image ne peut pas s’exécuter**  
  
 Le **/kernel** option et la **c** option fonctionnent indépendamment et aucune n’affecte les autres.  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /kernel dans Visual Studio  
  
1.  Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Dans le **des options supplémentaires** zone, ajoutez `/kernel` ou `/kernel-`.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)