---
title: Gestion d’exceptions x64
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 3d973354f94ca8c9f2e0901e60f2a8009ac08cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835049"
---
# <a name="x64-exception-handling"></a>Gestion d’exceptions x64

Vue d’ensemble de la gestion structurée des exceptions et des conventions de codage et du comportement de gestion des exceptions C++ sur le x64. Pour obtenir des informations générales sur la gestion des exceptions, consultez [gestion des exceptions dans Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Données de déroulement pour la gestion des exceptions, prise en charge du débogueur

Plusieurs structures de données sont requises pour la gestion des exceptions et la prise en charge du débogage.

### <a name="struct-runtime_function"></a>RUNTIME_FUNCTION, structure

La gestion des exceptions basée sur les tables requiert une entrée de table pour toutes les fonctions qui allouent de l’espace de pile ou appellent une autre fonction (par exemple, les fonctions non-feuille). Le format des entrées de la table de fonctions est le suivant :

|Taille|Valeur|
|-|-|
|ULONG|Adresse de début de la fonction|
|ULONG|Adresse de fin de la fonction|
|ULONG|Adresse des informations de déroulement|

La structure de RUNTIME_FUNCTION doit être alignée sur DWORD en mémoire. Toutes les adresses sont relatives à l’image, c’est-à-dire qu’elles sont des décalages de 32 bits par rapport à l’adresse de départ de l’image qui contient l’entrée de la table de fonctions. Ces entrées sont triées et placées dans la section. pdata d’une image PE32 +. Pour les fonctions générées dynamiquement [compilateurs JIT], le runtime pour prendre en charge ces fonctions doit utiliser RtlInstallFunctionTableCallback ou RtlAddFunctionTable pour fournir ces informations au système d’exploitation. Dans le cas contraire, la gestion des exceptions et le débogage des processus ne sont pas fiables.

### <a name="struct-unwind_info"></a>struct UNWIND_INFO

La structure d’informations sur les données de déroulement est utilisée pour enregistrer les effets d’une fonction sur le pointeur de pile, et où les registres non volatils sont enregistrés sur la pile :

|Taille|Valeur|
|-|-|
|UBYTE : 3|Version|
|UBYTE : 5|Indicateurs|
|UBYTE|Taille du prologue|
|UBYTE|Nombre de codes de déroulement|
|UBYTE : 4|Registre de frames|
|UBYTE : 4|Décalage du Registre du frame (mis à l’échelle)|
|USHORT \* n|Tableau des codes de déroulement|
|variable|Peut avoir la forme (1) ou (2) ci-dessous|

(1) gestionnaire d’exceptions

|Taille|Valeur|
|-|-|
|ULONG|Adresse du gestionnaire d’exceptions|
|variable|Données du gestionnaire spécifique à une langue (facultatif)|

(2) informations de déroulement chaînées

|Taille|Valeur|
|-|-|
|ULONG|Adresse de début de la fonction|
|ULONG|Adresse de fin de la fonction|
|ULONG|Adresse des informations de déroulement|

La structure de UNWIND_INFO doit être alignée sur DWORD en mémoire. Voici ce que signifie chaque champ :

- **Version**

   Numéro de version des données de déroulement, actuellement 1.

- **Indicateurs**

   Trois indicateurs sont actuellement définis :

   |Indicateur|Description|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La fonction a un gestionnaire d’exceptions qui doit être appelé lors de la recherche de fonctions qui doivent examiner des exceptions.|
   |`UNW_FLAG_UHANDLER`| La fonction a un gestionnaire de terminaison qui doit être appelé lors du déroulement d’une exception.|
   |`UNW_FLAG_CHAININFO`| Cette structure d’informations de déroulement n’est pas la structure principale de la procédure. Au lieu de cela, l’entrée d’informations de déroulement chaînées est le contenu d’une entrée de RUNTIME_FUNCTION précédente. Pour plus d’informations, consultez [structures d’informations de déroulement chaînées](#chained-unwind-info-structures). Si cet indicateur est défini, les indicateurs UNW_FLAG_EHANDLER et UNW_FLAG_UHANDLER doivent être effacés. En outre, le registre de frame et les champs d’allocation de pile fixe doivent avoir les mêmes valeurs que dans les informations de déroulement principales.|

- **Taille du prologue**

   Longueur du prologue de fonction en octets.

- **Nombre de codes de déroulement**

   Nombre d’emplacements dans le tableau des codes de déroulement. Certains codes de déroulement, par exemple UWOP_SAVE_NONVOL, requièrent plusieurs emplacements dans le tableau.

- **Registre de frames**

   Si la valeur est différente de zéro, la fonction utilise un pointeur de frame (FP) et ce champ est le numéro du Registre non volatil utilisé comme pointeur de frame, en utilisant le même codage pour le champ d’informations sur l’opération des nœuds de UNWIND_CODE.

- **Décalage du Registre du frame (mis à l’échelle)**

   Si le champ du registre des frames est différent de zéro, ce champ est le décalage à l’échelle de RSP appliqué au registre FP lorsqu’il est établi. Le registre FP réel est défini sur RSP + 16 \* ce nombre, ce qui permet de décaler de 0 à 240. Ce décalage permet de pointer le registre FP au milieu de l’allocation de pile locale pour les frames de pile dynamiques, ce qui permet une meilleure densité de code par le biais d’instructions plus courtes. (Autrement dit, d’autres instructions peuvent utiliser le format de décalage signé 8 bits.)

- **Tableau des codes de déroulement**

   Tableau d’éléments qui explique l’effet du prologue sur les registres non volatils et RSP. Reportez-vous à la section sur UNWIND_CODE pour obtenir la signification des éléments individuels. À des fins d’alignement, ce tableau a toujours un nombre pair d’entrées, et l’entrée finale est potentiellement inutilisée. Dans ce cas, le tableau est plus long que ce qui est indiqué par le champ nombre de codes de déroulement.

- **Adresse du gestionnaire d’exceptions**

   Pointeur relatif à une image vers le gestionnaire d’exceptions ou d’arrêt spécifique au langage de la fonction, si l’indicateur UNW_FLAG_CHAININFO est clair et que l’un des indicateurs UNW_FLAG_EHANDLER ou UNW_FLAG_UHANDLER est défini.

- **Données du gestionnaire spécifique au langage**

   Données du gestionnaire d’exceptions spécifiques au langage de la fonction. Le format de ces données n’est pas spécifié et est entièrement déterminé par le gestionnaire d’exceptions spécifique utilisé.

- **Informations de déroulement chaînées**

   Si l’indicateur UNW_FLAG_CHAININFO est défini, la structure de UNWIND_INFO se termine par trois UWORDs.  Ces UWORDs représentent les informations de RUNTIME_FUNCTION pour la fonction du déroulement chaîné.

### <a name="struct-unwind_code"></a>struct UNWIND_CODE

Le tableau de codes de déroulement est utilisé pour enregistrer la séquence d’opérations dans le prologue qui affectent les registres non volatils et RSP. Chaque élément de code a le format suivant :

|Taille|Valeur|
|-|-|
|UBYTE|Décalage dans le prologue|
|UBYTE : 4|Code d’opération de déroulement|
|UBYTE : 4|Informations sur l’opération|

Le tableau est trié par ordre décroissant de décalage dans le prologue.

#### <a name="offset-in-prolog"></a>Décalage dans le prologue

Offset (à partir du début du prologue) de la fin de l’instruction qui effectue cette opération, plus 1 (autrement dit, l’offset du début de l’instruction suivante).

#### <a name="unwind-operation-code"></a>Code d’opération de déroulement

Remarque : certains codes d’opération requièrent un décalage non signé vers une valeur dans le frame de pile local. Cet offset est compris entre le début, c’est-à-dire l’adresse la plus basse de l’allocation de pile fixe. Si le champ du registre des frames dans le UNWIND_INFO est égal à zéro, cet offset provient de RSP. Si le champ du registre des frames est différent de zéro, il s’agit de l’emplacement à partir duquel RSP a été trouvé lors de l’établissement du Registre FP. Il est égal au registre FP moins le décalage du Registre FP (16 \* le décalage du registre de frames mis à l’échelle dans le UNWIND_INFO). Si un registre FP est utilisé, tout code de déroulement qui prend un offset doit être utilisé uniquement après l’établissement du Registre FP dans le prologue.

Pour tous les OpCodes à l’exception de `UWOP_SAVE_XMM128` et `UWOP_SAVE_XMM128_FAR` , le décalage est toujours un multiple de 8, car toutes les valeurs de pile d’intérêt sont stockées sur des limites de 8 octets (la pile elle-même est toujours alignée sur 16 octets). Pour les codes d’opération qui prennent un décalage bref (inférieur à 512 Ko), le dernier USHORT des nœuds pour ce code contient le décalage divisé par 8. Pour les codes d’opération qui prennent un décalage long (512 Ko <= décalage < 4 Go), les deux derniers nœuds USHORT pour ce code contiennent le décalage (au format Little endian).

Pour les OpCodes `UWOP_SAVE_XMM128` et `UWOP_SAVE_XMM128_FAR` , le décalage est toujours un multiple de 16, étant donné que toutes les opérations XMM 128 bits doivent se produire sur une mémoire alignée sur 16 octets. Par conséquent, un facteur d’échelle de 16 est utilisé pour `UWOP_SAVE_XMM128` , en autorisant des décalages inférieurs à 1M.

Le code d’opération de déroulement est l’une des valeurs suivantes :

- `UWOP_PUSH_NONVOL` (0) 1 nœud

  Exécute un push d’un registre entier non volatil, en décrémentant RSP de 8. Les informations sur l’opération sont le numéro du Registre. En raison des contraintes sur les épilogues, `UWOP_PUSH_NONVOL` les codes de déroulement doivent apparaître en premier dans le prologue et en conséquence, en dernier dans le tableau de codes de déroulement. Ce classement relatif s’applique à tous les autres codes de déroulement, à l’exception de `UWOP_PUSH_MACHFRAME` .

- `UWOP_ALLOC_LARGE` (1) 2 ou 3 nœuds

  Allouez une zone de grande taille sur la pile. Il existe deux formes. Si les informations sur l’opération sont égales à 0, la taille de l’allocation divisée par 8 est enregistrée dans l’emplacement suivant, ce qui permet une allocation allant jusqu’à 512 Ko-8. Si les informations sur l’opération sont égales à 1, la taille non mise à l’échelle de l’allocation est enregistrée dans les deux emplacements suivants au format Little endian, ce qui permet d’allouer jusqu’à 4 Go-8.

- `UWOP_ALLOC_SMALL` (2) 1 nœud

  Allouez une zone de petite taille sur la pile. La taille de l’allocation est le champ d’informations sur l’opération \* 8 + 8, ce qui permet d’allouer de 8 à 128 octets.

  Le code de déroulement pour une allocation de pile doit toujours utiliser le plus petit encodage possible :

  |**Taille d’allocation**|**Code de déroulement**|
  |-|-|
  |8 à 128 octets|`UWOP_ALLOC_SMALL`|
  |136 à 512 Ko-8 octets|`UWOP_ALLOC_LARGE`, informations sur l’opération = 0|
  |512 Ko à 4G-8 octets|`UWOP_ALLOC_LARGE`, informations sur l’opération = 1|

- `UWOP_SET_FPREG` (3) 1 nœud

  Établissez le Registre du pointeur de frame en affectant au registre un décalage de la RSP actuelle. Le décalage est égal au champ décalage du Registre du frame (mis à l’échelle) dans le UNWIND_INFO \* 16, ce qui permet de décaler de 0 à 240. L’utilisation d’un décalage permet d’établir un pointeur de frame qui pointe vers le milieu de l’allocation de pile fixe, ce qui contribue à la densité de code en permettant à d’autres accès d’utiliser des formes d’instructions courtes. Le champ informations sur l’opération est réservé et ne doit pas être utilisé.

- `UWOP_SAVE_NONVOL` (4) 2 nœuds

  Enregistrez un registre entier non volatile sur la pile à l’aide d’un MOV au lieu d’un PUSH. Ce code est principalement utilisé pour l' *encapsulage*, où un registre non volatil est enregistré dans la pile à une position précédemment allouée. Les informations sur l’opération sont le numéro du Registre. Le décalage de la pile mis à l’échelle par 8 est enregistré dans l’emplacement du code de l’opération de déroulement suivant, comme décrit dans la remarque ci-dessus.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 nœuds

  Enregistrez un registre entier non volatile sur la pile avec un décalage long, à l’aide d’un MOV au lieu d’un PUSH. Ce code est principalement utilisé pour l' *encapsulage*, où un registre non volatil est enregistré dans la pile à une position précédemment allouée. Les informations sur l’opération sont le numéro du Registre. Le décalage de la pile non mis à l’échelle est enregistré dans les deux emplacements de code d’opération de déroulement suivants, comme décrit dans la remarque ci-dessus.

- `UWOP_SAVE_XMM128` (8) 2 nœuds

  Enregistrez tous les 128 bits d’un registre XMM non volatil sur la pile. Les informations sur l’opération sont le numéro du Registre. Le décalage de la pile mis à l’échelle par 16 est enregistré dans l’emplacement suivant.

- `UWOP_SAVE_XMM128_FAR` (9) 3 nœuds

  Enregistrez tous les 128 bits d’un registre XMM non volatil sur la pile avec un décalage long. Les informations sur l’opération sont le numéro du Registre. Le décalage de la pile non mis à l’échelle est enregistré dans les deux emplacements suivants.

- `UWOP_PUSH_MACHFRAME` (10) 1 nœud

  Exécute un push d’un frame de machine.  Ce code de déroulement est utilisé pour enregistrer l’effet d’une interruption ou d’une exception matérielle. Il existe deux formes. Si les informations sur l’opération sont égales à 0, l’un de ces frames a fait l’objet d’un push sur la pile :

  |Emplacement|Valeur|
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|Ancien RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|PROTOCOLES|

  Si les informations sur l’opération sont égales à 1, cela signifie que l’un de ces frames a fait l’objet d’un push :

  |Emplacement|Valeur|
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|Ancien RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|PROTOCOLES|
  |RSP|Code d'erreur|

  Ce code de déroulement apparaît toujours dans un prologue factice, qui n’est jamais réellement exécuté, mais il apparaît à la place avant le point d’entrée réel d’une routine d’interruption, et existe uniquement pour fournir un emplacement pour simuler la transmission de type push d’un frame de machine. `UWOP_PUSH_MACHFRAME` enregistre cette simulation, qui indique que l’ordinateur a effectué cette opération de manière conceptuelle :

  1. Adresse de retour RIP du haut de la pile dans *temp*
  
  1. Push SS

  1. Envoyer l’ancien RSP

  1. EFLAGS Push

  1. Notifications push CS

  1. Envoi *temporaire*

  1. Code d’erreur push (si les informations d’op sont égales à 1)

  L’opération simulée `UWOP_PUSH_MACHFRAME` DÉCRÉMENTE RSP de 40 (op info est égal à 0) ou 48 (op info est égal à 1).

#### <a name="operation-info"></a>Informations sur l’opération

La signification des bits d’informations sur l’opération dépend du code d’opération. Pour encoder un registre à usage général (entier), ce mappage est utilisé :

|bit|S’inscrire|
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 à 15|R8 à R15|

### <a name="chained-unwind-info-structures"></a>Structures d’informations de déroulement chaînées

Si l’indicateur de UNW_FLAG_CHAININFO est défini, une structure d’informations de déroulement est une structure secondaire et le champ de l’adresse du gestionnaire d’exceptions partagées/des informations chaînées contient les informations de déroulement principales. Cet exemple de code extrait les informations de déroulement principales, en supposant que `unwindInfo` est la structure avec l’indicateur UNW_FLAG_CHAININFO défini.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Les informations chaînées sont utiles dans deux situations. Tout d’abord, elle peut être utilisée pour les segments de code non contigus. En utilisant des informations chaînées, vous pouvez réduire la taille des informations de déroulement requises, car vous n’avez pas besoin de dupliquer le tableau des codes de déroulement à partir des informations de déroulement principales.

Vous pouvez également utiliser des informations chaînées pour regrouper les enregistrements de Registre volatils. Le compilateur peut retarder l’enregistrement de certains registres volatiles jusqu’à ce qu’il se trouve en dehors du prologue d’entrée de fonction. Vous pouvez les enregistrer en ayant des informations de déroulement principales pour la partie de la fonction avant le code groupé, puis en configurant les informations chaînées avec une taille différente de zéro, où les codes de déroulement dans les informations chaînées reflètent les enregistrements des registres non volatiles. Dans ce cas, les codes de déroulement sont toutes des instances de UWOP_SAVE_NONVOL. Un regroupement qui enregistre des registres non volatils à l’aide d’un PUSH ou modifie le registre RSP à l’aide d’une allocation de pile fixe supplémentaire n’est pas pris en charge.

Un élément de UNWIND_INFO qui a UNW_FLAG_CHAININFO jeu peut contenir une entrée de RUNTIME_FUNCTION dont l’élément UNWIND_INFO a également UNW_FLAG_CHAININFO défini, parfois appelé *plusieurs retours à*la ligne. Enfin, les pointeurs d’informations de déroulement chaînés arrivent à un UNWIND_INFO élément dont l’UNW_FLAG_CHAININFO a été effacé. Cet élément est l’élément de UNWIND_INFO principal, qui pointe vers le point d’entrée de procédure réel.

## <a name="unwind-procedure"></a>Procédure de déroulement

Le tableau de codes de déroulement est trié par ordre décroissant. Lorsqu’une exception se produit, le contexte complet est stocké par le système d’exploitation dans un enregistrement de contexte. La logique de distribution des exceptions est ensuite appelée, ce qui exécute à plusieurs reprises ces étapes pour rechercher un gestionnaire d’exceptions :

1. Utilisez le RIP actuel stocké dans l’enregistrement de contexte pour rechercher une entrée de table RUNTIME_FUNCTION qui décrit la fonction active (ou la partie de fonction pour les entrées UNWIND_INFO chaînées).

1. Si aucune entrée de table de fonctions n’est trouvée, elle se trouve dans une fonction feuille et RSP traite directement le pointeur de retour. Le pointeur de retour sur [RSP] est stocké dans le contexte mis à jour, le RSP simulé est incrémenté de 8, et l’étape 1 est répétée.

1. Si une entrée de table de fonctions est trouvée, le RIP peut se trouver dans trois régions : a) dans un épilogue, b) dans le prologue, ou c) dans le code qui peut être couvert par un gestionnaire d’exceptions.

   - Cas a) si le RIP se trouve dans un épilogue, alors que le contrôle quitte la fonction, aucun gestionnaire d’exceptions ne peut être associé à cette exception pour cette fonction, et les effets de l’épilogue doivent être poursuivis pour calculer le contexte de la fonction d’appelant. Pour déterminer si le RIP se trouve dans un épilogue, le flux de code du RIP est examiné. Si ce flux de code peut être mis en correspondance avec la partie de fin d’un épilogue légitime, il se trouve dans un épilogue, et la partie restante de l’épilogue est simulée, avec l’enregistrement de contexte mis à jour lors du traitement de chaque instruction. Après ce traitement, l’étape 1 est répétée.

   - Cas b) si le RIP se trouve dans le prologue, alors que le contrôle n’a pas entré la fonction, aucun gestionnaire d’exceptions ne peut être associé à cette exception pour cette fonction, et les effets du prologue doivent être annulés pour calculer le contexte de la fonction d’appelant. Le RIP est dans le prologue si la distance entre la fonction et le RIP est inférieure ou égale à la taille du prologue encodée dans les informations de déroulement. Les effets du prologue sont déroulés en balayant vers l’avant le tableau des codes de déroulement pour la première entrée avec un offset inférieur ou égal au décalage de l’extraction à partir du début de la fonction, puis en annulant l’effet de tous les éléments restants dans le tableau de codes de déroulement. L’étape 1 est ensuite répétée.

   - Cas c) si le RIP ne fait pas partie d’un prologue ou d’un épilogue, et que la fonction a un gestionnaire d’exceptions (UNW_FLAG_EHANDLER est défini), le gestionnaire spécifique au langage est appelé. Le gestionnaire analyse ses données et appelle les fonctions de filtre en fonction des besoins. Le gestionnaire spécifique au langage peut retourner que l’exception a été gérée ou que la recherche doit être poursuivie. Elle peut également initier un déroulement directement.

1. Si le gestionnaire propre au langage retourne un état géré, l’exécution se poursuit à l’aide de l’enregistrement de contexte d’origine.

1. S’il n’existe pas de gestionnaire spécifique à une langue ou si le gestionnaire retourne un État « continuer la recherche », l’enregistrement de contexte doit être déroulé à l’état de l’appelant. Pour ce faire, vous traitez tous les éléments du tableau de code de déroulement, en annulant l’effet de chacun d’entre eux. L’étape 1 est ensuite répétée.

Lorsque les informations de déroulement chaînées sont impliquées, ces étapes de base sont toujours suivies. La seule différence est que, lorsque vous parcourez le tableau de code de déroulement pour dérouler les effets d’un prologue, lorsque la fin du tableau est atteinte, il est ensuite lié aux informations de déroulement parent et le tableau de code de déroulement entier trouvé est parcouru. Cette liaison continue jusqu’à parvenir à des informations de déroulement sans l’indicateur UNW_CHAINED_INFO, puis elle finit par parcourir son tableau de code de déroulement.

Le plus petit ensemble de données de déroulement est de 8 octets. Cela représente une fonction qui n’a alloué que 128 octets de la pile ou moins, et qui a peut-être enregistré un registre non volatile. C’est également la taille d’une structure d’informations de déroulement chaîné pour un prologue de longueur nulle sans code de déroulement.

## <a name="language-specific-handler"></a>Gestionnaire spécifique au langage

L’adresse relative du gestionnaire spécifique au langage est présente dans le UNWIND_INFO chaque fois que les indicateurs UNW_FLAG_EHANDLER ou UNW_FLAG_UHANDLER sont définis. Comme décrit dans la section précédente, le gestionnaire spécifique au langage est appelé dans le cadre de la recherche d’un gestionnaire d’exceptions ou dans le cadre d’un déroulement. Il a ce prototype :

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** fournit un pointeur vers un enregistrement d’exception, qui a la définition Win64 standard.

**EstablisherFrame** est l’adresse de la base de l’allocation de pile fixe pour cette fonction.

**ContextRecord** pointe vers le contexte d’exception au moment où l’exception a été levée (dans le cas du gestionnaire d’exceptions) ou dans le contexte de « déroulement » actuel (dans le cas du gestionnaire de terminaisons).

**DispatcherContext** pointe vers le contexte du répartiteur pour cette fonction. Il a cette définition :

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** est la valeur de RIP dans cette fonction. Cette valeur est soit une adresse d’exception, soit l’adresse à laquelle le contrôle a quitté la fonction d’établissement. Le RIP est utilisé pour déterminer si le contrôle se trouve dans une construction protégée à l’intérieur de cette fonction, par exemple un `__try` bloc pour `__try` / **`__except`** ou `__try` / **`__finally`** .

**ImageBase** est la base d’image (adresse de chargement) du module contenant cette fonction, à ajouter aux offsets 32 bits utilisés dans l’entrée de fonction et les informations de déroulement pour enregistrer les adresses relatives.

**FunctionEntry** fournit un pointeur vers l’entrée de fonction RUNTIME_FUNCTION qui contient les informations relatives à la fonction et au déroulement image de base de cette fonction.

**EstablisherFrame** est l’adresse de la base de l’allocation de pile fixe pour cette fonction.

**TargetIp** Fournit une adresse d’instruction facultative qui spécifie l’adresse de continuation du déroulement. Cette adresse est ignorée si **EstablisherFrame** n’est pas spécifié.

**ContextRecord** pointe vers le contexte d’exception, pour une utilisation par le code de dispatch/déroulement de l’exception système.

**LanguageHandler** pointe vers la routine du gestionnaire de langage spécifique au langage qui est appelée.

**HandlerData** pointe vers les données de gestionnaire spécifiques au langage pour cette fonction.

## <a name="unwind-helpers-for-masm"></a>Dérouler des applications d’assistance pour MASM

Pour écrire les routines d’assembly appropriées, il existe un ensemble de Pseudo-opérations qui peuvent être utilisées en parallèle avec les instructions d’assembly réelles pour créer les. pdata et. XData appropriés. Et il existe un ensemble de macros qui fournissent une utilisation simplifiée des pseudo-opérations pour leurs utilisations les plus courantes.

### <a name="raw-pseudo-operations"></a>Pseudo-opérations brutes

|Pseudo-opération|Description|
|-|-|
|FRAME de PROC \[ . :*ehandler*]|Fait en sorte que MASM génère une entrée de table de fonctions dans. pdata et les informations de déroulement dans. XData pour le comportement de déroulement de la gestion structurée des exceptions d’une fonction.  Si *ehandler* est présent, cette procédure est entrée dans le. XData comme gestionnaire spécifique au langage.<br /><br /> Lorsque l’attribut FRAME est utilisé, il doit être suivi d’un. Directive ENDPROLOG.  Si la fonction est une fonction feuille (telle que définie dans les [types de fonction](../build/stack-usage.md#function-types)), l’attribut Frame n’est pas nécessaire, comme le reste de ces pseudo-opérations.|
|. *Registre* PUSHREG|Génère une entrée de code de déroulement UWOP_PUSH_NONVOL pour le numéro de Registre spécifié à l’aide de l’offset actuel dans le prologue.<br /><br /> Utilisez-le uniquement avec des registres d’entiers non volatils.  Pour les notifications push de registres volatils, utilisez un. ALLOCSTACK 8, à la place|
|. *Registre*SETFRAME, *décalage*|Remplit le champ du Registre du frame et le décalage dans les informations de déroulement à l’aide du Registre et de l’offset spécifiés. Le décalage doit être un multiple de 16 et inférieur ou égal à 240. Cette directive génère également une entrée de code de déroulement UWOP_SET_FPREG pour le registre spécifié à l’aide de l’offset de prologue actuel.|
|. *Taille* de ALLOCSTACK|Génère un UWOP_ALLOC_SMALL ou un UWOP_ALLOC_LARGE avec la taille spécifiée pour l’offset actuel dans le prologue.<br /><br /> L’opérande de *taille* doit être un multiple de 8.|
|. *Registre*SAVEREG, *décalage*|Génère un UWOP_SAVE_NONVOL ou une entrée de code de déroulement UWOP_SAVE_NONVOL_FAR pour le registre et l’offset spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.<br /><br /> *offset* doit être positif et un multiple de 8. l' *offset* est relatif à la base du frame de la procédure, qui est généralement dans RSP ou, si vous utilisez un pointeur de frame, le pointeur de frame non mis à l’échelle.|
|. *Registre*SAVEXMM128, *décalage*|Génère un UWOP_SAVE_XMM128 ou une entrée de code de déroulement UWOP_SAVE_XMM128_FAR pour le registre XMM et le décalage spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.<br /><br /> *offset* doit être positif et un multiple de 16.  l' *offset* est relatif à la base du frame de la procédure, qui est généralement dans RSP ou, si vous utilisez un pointeur de frame, le pointeur de frame non mis à l’échelle.|
|. \[ *Code*PUSHFRAME]|Génère une entrée de code de déroulement UWOP_PUSH_MACHFRAME. Si le *code* facultatif est spécifié, le modificateur 1 est attribué à l’entrée du code de déroulement. Sinon, le modificateur est 0.|
|.ENDPROLOG|Signale la fin des déclarations de prologue.  Doit se produire dans les 255 premiers octets de la fonction.|

Voici un exemple de prologue de fonction avec une utilisation correcte de la plupart des OpCodes :

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

Pour plus d’informations sur l’exemple d’épilogue, consultez [code d’épilogue](prolog-and-epilog.md#epilog-code) dans le [prologue x64 et épilogue](prolog-and-epilog.md).

### <a name="masm-macros"></a>MASM (macros)

Pour simplifier l’utilisation des [Pseudo-opérations brutes](#raw-pseudo-operations), il existe un ensemble de macros, défini dans ksamd64. Inc, qui peut être utilisé pour créer des prologues et des épilogues de procédure classiques.

|Macro|Description|
|-|-|
|alloc_stack (n)|Alloue un frame de pile de n octets (à l’aide de `sub rsp, n` ) et émet les informations de déroulement appropriées (. allocstack n)|
|save_reg *reg*, *loc*|Enregistre *un registre de registres non* volatil sur la pile à l’emplacement RSP offset *loc*et émet les informations de déroulement appropriées. (. savereg reg, loc)|
|push_reg *reg*|Exécute un *push d’un registre de registres non* volatil sur la pile et émet les informations de déroulement appropriées. (. pushreg reg)|
|rex_push_reg *reg*|Enregistre un registre non volatil sur la pile à l’aide d’un push de 2 octets et émet les informations de déroulement appropriées (. pushreg reg).  Utilisez cette macro si l’envoi est la première instruction de la fonction, afin de garantir que la fonction peut être corrigée à chaud.|
|save_xmm128 *reg*, *loc*|Enregistre un fichier de Registre XMM non *volatil sur la* pile à l’emplacement RSP offset *loc*et émet les informations de déroulement appropriées (. savexmm128 reg, loc)|
|set_frame *reg*, *décalage*|Définit *la valeur de* Registre du registre des frames sur le *décalage* RSP + (à l’aide d’un `mov` , ou `lea` ) et émet les informations de déroulement appropriées (. set_frame reg, offset)|
|push_eflags|Exécute un push du eflags avec une `pushfq` instruction et émet les informations de déroulement appropriées (. alloc_stack 8)|

Voici un exemple de prologue de fonction avec une utilisation correcte des macros :

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Dérouler les définitions de données en C

Voici une description C des données de déroulement :

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)
