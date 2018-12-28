---
title: x64 la gestion des exceptions
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 33206dfb885239839c3a64436b6b540fc7d4e6e5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627538"
---
# <a name="x64-exception-handling"></a>x64 la gestion des exceptions

Vue d’ensemble de la gestion structurée des exceptions et les conventions de codage et comportement sur le x64 des exceptions C++. Pour obtenir des informations générales sur la gestion des exceptions, consultez [gestion des exceptions dans Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Données pour la gestion des exceptions, prise en charge du débogueur de déroulement

Plusieurs structures de données sont requises pour la gestion des exceptions et la prise en charge le débogage.

### <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION, structure

Gestion des exceptions basée sur une table nécessite une entrée de table pour toutes les fonctions qui allouent des espace de pile ou appellent une autre fonction (par exemple, les fonctions non-feuille). Les entrées de table de fonction ont le format :

|||
|-|-|
|ULONG|Adresse de début (fonction)|
|ULONG|Adresse de fin (fonction)|
|ULONG|Adresse des informations de déroulement|

La structure RUNTIME_FUNCTION doit être DWORD aligné en mémoire. Toutes les adresses sont relatives à l’image, autrement dit, ils sont des décalages de 32 bits à partir de l’adresse de départ de l’image qui contient l’entrée de table de fonction. Ces entrées sont triées et placées dans la section .pdata d’une image PE32 +. Pour les fonctions générées dynamiquement [compilateurs JIT], le runtime pour prendre en charge ces fonctions doit utiliser RtlInstallFunctionTableCallback ou RtlAddFunctionTable pour fournir ces informations pour le système d’exploitation. Cela entraîne non fiables gestion des exceptions et débogage de processus.

### <a name="struct-unwindinfo"></a>struct UNWIND_INFO

La structure d’informations de données de déroulement est utilisée pour enregistrer les effets de qu'une fonction a sur le pointeur de pile et où les registres non volatils sont enregistrés sur la pile :

|||
|-|-|
|UBYTE : 3|Version|
|UBYTE : 5|Indicateurs|
|UBYTE|Taille du prologue|
|UBYTE|Nombre de codes de déroulement|
|UBYTE : 4|Registre du frame|
|UBYTE : 4|Décalage de trame du Registre (mis à l’échelle)|
|USHORT \* n|Tableau de codes de déroulement|
|variable|Peut être de forme (1) ou (2) ci-dessous|

(1) Gestionnaire d’exceptions

|||
|-|-|
|ULONG|Adresse du Gestionnaire d’exceptions|
|variable|Données de gestionnaire spécifique au langage (facultatives)|

(2) chaînées informations de déroulement

|||
|-|-|
|ULONG|Adresse de début (fonction)|
|ULONG|Adresse de fin (fonction)|
|ULONG|Adresse des informations de déroulement|

La structure UNWIND_INFO doit être DWORD aligné en mémoire. Voici ce que signifie chaque champ :

- **Version**

   Numéro de version des données de déroulement, 1 actuellement.

- **indicateurs**

   Trois indicateurs sont actuellement définis :

   |Indicateur|Description|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La fonction a un gestionnaire d’exceptions qui doit être appelé lors de la recherche pour les fonctions que vous avez besoin d’examiner les exceptions.|
   |`UNW_FLAG_UHANDLER`| La fonction a un gestionnaire de terminaisons qui doit être appelé lors du déroulement d’une exception.|
   |`UNW_FLAG_CHAININFO`| Cette structure n’est pas le principal pour la procédure d’informations de déroulement. Au lieu de cela, les informations de déroulement chaînées entrée est le contenu d’une entrée RUNTIME_FUNCTION antérieure. Pour plus d’informations, consultez [structures d’informations de déroulement chaînées](#chained-unwind-info-structures). Si cet indicateur est défini, les indicateurs UNW_FLAG_EHANDLER et UNW_FLAG_UHANDLER doivent être effacées. En outre, les champs de d’allocation de Registre et de pile fixe frame doivent avoir les mêmes valeurs que dans le réplica principal d’informations de déroulement.|

- **Taille du prologue**

   Longueur du prologue de fonction en octets.

- **Nombre de codes de déroulement**

   Le nombre d’emplacements dans le tableau de codes de déroulement. Certains codes de déroulement, par exemple, UWOP_SAVE_NONVOL, nécessitent plus d’un emplacement dans le tableau.

- **Registre du frame**

   Si elle est différente de zéro, la fonction utilise un pointeur de frame (FP), et ce champ est le nombre de Registre non volatil utilisé comme pointeur de frame, à l’aide de l’encodage même pour le champ d’information opération des nœuds UNWIND_CODE.

- **Registre du frame décalage (mis à l’échelle)**

   Si le champ du Registre du frame est différent de zéro, ce champ est le décalage à l’échelle de RSP qui est appliqué à FP inscrire lorsqu’il est établi. Le registre FP réel a la valeur RSP + 16 \* ce nombre, autorisant des offsets compris entre 0 et 240. Ce décalage permet pointant vers le registre FP au milieu de l’allocation de pile locale pour les frames de pile dynamique, ce qui permet une meilleure densité de code via des instructions plus courtes (davantage d’instructions permettre utiliser le format d’offset signé 8 bits).

- **Tableau de codes de déroulement**

   Un tableau d’éléments qui explique l’effet du prologue sur les registres non volatils et RSP. Consultez la section sur UNWIND_CODE pour la signification des différents éléments. À des fins d’alignement, ce tableau a toujours un nombre pair d’entrées, et la dernière entrée est potentiellement inutilisée. Dans ce cas, le tableau est une plus longue que ceux indiqués par le nombre de champs de codes de déroulement.

- **Adresse du Gestionnaire d’exceptions**

   Un pointeur relatif à l’image de la fonction exception spécifique au langage ou Gestionnaire de terminaisons, si l’indicateur UNW_FLAG_CHAININFO est désactivé et un des indicateurs UNW_FLAG_EHANDLER ou UNW_FLAG_UHANDLER est défini.

- **Données du gestionnaire spécifique au langage**

   Données de gestionnaire d’exception spécifique au langage de la fonction. Le format de ces données est non spécifié et complètement déterminé par le Gestionnaire d’exceptions spécifiques en cours d’utilisation.

- **Chaîne d’informations de déroulement**

   Si l’indicateur UNW_FLAG_CHAININFO est défini la structure UNWIND_INFO se termine par trois UWORD.  Ces UWORD représentent les informations RUNTIME_FUNCTION pour la fonction du déroulement chaîné.

### <a name="struct-unwindcode"></a>struct UNWIND_CODE

Le tableau des codes de déroulement est utilisé pour enregistrer la séquence des opérations dans le prologue qui affectent les registres non volatils et RSP. Chaque élément de code a ce format :

|||
|-|-|
|UBYTE|Offset dans le prologue|
|UBYTE : 4|Code d’opération de déroulement|
|UBYTE : 4|Informations sur l’opération|

Le tableau est trié par ordre décroissant d’offset dans le prologue.

#### <a name="offset-in-prolog"></a>Offset dans le prologue

Décalage à partir du début du prologue de la fin de l’instruction qui effectue cette opération, plus 1 (autrement dit, le décalage du début de l’instruction suivante).

#### <a name="unwind-operation-code"></a>Code d’opération de déroulement

Remarque : Certains codes d’opération exigent un offset non signé à une valeur dans le frame de pile locales. Ce décalage est dès le départ, autrement dit, l’adresse la plus basse de l’allocation de pile fixe. Si le champ du Registre du Frame dans UNWIND_INFO est égal à zéro, ce décalage est from RSP. Si le champ du Registre du Frame est différent de zéro, il s’agit de l’offset à partir d’où se situait RSP lorsque le registre FP a été établi. Cela équivaut au registre FP moins l’offset du Registre FP (16 \* offset du Registre le frame à l’échelle dans UNWIND_INFO). Si un registre FP est utilisé, puis n’importe quel code de déroulement prenant un offset doit uniquement servir une fois le registre FP est établi dans le prologue.

Pour tous les opcodes sauf `UWOP_SAVE_XMM128` et `UWOP_SAVE_XMM128_FAR`, l’offset est toujours un multiple de 8, car tous de la pile des valeurs d’intérêt sont stockées sur des limites de 8 octets (la pile proprement dite est toujours alignée sur 16 octets). Pour les codes d’opération qui prennent un offset court (moins de 512 Ko), le dernier USHORT dans les nœuds pour ce code conserve l’offset divisé par 8. Pour les codes d’opération qui prennent un offset long (512 Ko < = décalage < 4 Go), les deux nœuds USHORT finals pour ce code contiennent le décalage (en format little-endian).

Pour les opcodes `UWOP_SAVE_XMM128` et `UWOP_SAVE_XMM128_FAR`, l’offset est toujours un multiple de 16, car toutes les opérations XMM de 128 bits doivent se produire sur mémoire alignée sur 16 octets. Par conséquent, un facteur d’échelle de 16 est utilisé pour `UWOP_SAVE_XMM128`, autorisant des offsets de moins de 1 M.

Le code d’opération de déroulement est une des valeurs suivantes :

- `UWOP_PUSH_NONVOL` (0) 1 nœud

  Envoyez un registre entier non volatil, en décrémentant RSP de 8. Les informations de l’opération sont le numéro de l’historique. En raison de contraintes sur les épilogues, `UWOP_PUSH_NONVOL` codes de déroulement doivent apparaître en premier dans le prologue et également en dernier dans le tableau des codes de déroulement. Ce classement relatif s’applique à tous les autres codes de déroulement à l’exception `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 ou 3 nœuds

  Allouez une zone de grande taille sur la pile. Il existe deux formes. Si les informations de l’opération est égale à 0, alors que la taille de l’allocation divisée par 8 est enregistrée dans l’emplacement suivant, en autorisant une allocation jusqu'à 512 Ko - 8. Si les informations de l’opération est égal à 1, la taille non ajustée de l’allocation est enregistrée dans les deux emplacements dans un format little-endian, ce qui permet les allocations jusqu'à 4 Go - 8.

- `UWOP_ALLOC_SMALL` (2) nœud 1

  Allouez une zone de petite taille sur la pile. La taille de l’allocation est le champ informations opération \* 8 + 8, autorisant les allocations de 8 à 128 octets.

  Le code de déroulement pour une allocation de pile doit toujours utiliser l’encodage le plus court possible :

  |**Taille d’allocation**|**Code de déroulement**|
  |-|-|
  |8 à 128 octets|`UWOP_ALLOC_SMALL`|
  |136 à 512 Ko - 8 octets|`UWOP_ALLOC_LARGE`, informations sur l’opération = 0|
  |512 Ko à 4 Go - 8 octets|`UWOP_ALLOC_LARGE`, informations sur l’opération = 1|

- `UWOP_SET_FPREG` (3) 1 nœud

  Établir le Registre de pointeur de frame en définissant le Registre à un certain offset du RSP actuel. Le décalage est égal au champ de l’offset du Registre du Frame (mis à l’échelle) dans UNWIND_INFO \* 16, ce qui permet des offsets de 0 à 240. L’utilisation d’un offset autorise l’établissement d’un pointeur de frame qui pointe vers le milieu de la pile allocation fixe, permettant ainsi de densité de code en permettant à plus d’accès à utiliser des formulaires d’instruction courts. Le champ informations opération est réservé et ne doit pas être utilisé.

- `UWOP_SAVE_NONVOL` (4) 2 nœuds

  Enregistrez un registre entier non volatil sur la pile à l’aide de MOV au lieu d’un PUSH. Ce code est principalement utilisé pour *rétraction*, où un Registre non volatil est enregistré à la pile dans une position qui a été précédemment allouée. Les informations de l’opération sont le numéro de l’historique. Le décalage de la pile de mise à l’échelle par 8 est enregistré dans l’autre emplacement de code d’opération de déroulement, comme décrit dans la Remarque ci-dessus.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 nœuds

  Enregistrez un registre entier non volatil sur la pile avec un offset long, à l’aide de MOV au lieu d’un PUSH. Ce code est principalement utilisé pour *rétraction*, où un Registre non volatil est enregistré à la pile dans une position qui a été précédemment allouée. Les informations de l’opération sont le numéro de l’historique. Le décalage de la pile sans échelle est enregistré aux deux emplacements de code d’opération de déroulement comme décrit dans la Remarque ci-dessus.

- `UWOP_SAVE_XMM128` (8) nœuds 2

  Enregistrez les 128 bits d’un registre XMM non volatil sur la pile. Les informations de l’opération sont le numéro de l’historique. L’offset de la pile de mise à l’échelle par 16 est enregistré dans l’emplacement suivant.

- `UWOP_SAVE_XMM128_FAR` (9) 3 nœuds

  Enregistrez les 128 bits d’un registre XMM non volatil sur la pile avec un offset long. Les informations de l’opération sont le numéro de l’historique. L’offset de pile non ajustée est enregistrée dans les deux emplacements.

- `UWOP_PUSH_MACHFRAME` (10) nœud 1

  Envoyer une image de machine.  Cela sert à enregistrer l’effet d’une interruption matérielle ou d’exception. Il existe deux formes. Si les informations de l’opération est égale à 0, un de ces frames a été ajouté à la pile :

  |||
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|Ancien RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|RIP|

  Si les informations de l’opération est égale à 1, un de ces frames ont été envoyé :

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|Ancien RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|RIP|
  |RSP|Code d'erreur|

  Ce code de déroulement s’affiche toujours dans un prologue factice, ce qui n’est jamais réellement exécuté, mais au lieu de cela apparaît avant le point d’entrée réelle d’une routine d’interruption et existe uniquement pour fournir un emplacement pour simuler le push d’un frame de la machine. `UWOP_PUSH_MACHFRAME` enregistre cette simulation, ce qui indique que l’ordinateur a effectuée sur le plan conceptuel de cette opération :

  1. Affiche l’adresse de retour de RIP à partir du haut de la pile dans *Temp*
  
  1. Push SS

  1. Push ancien RSP

  1. Push EFLAGS

  1. Push CS

  1. Push *Temp*

  1. Envoyer le Code d’erreur (si l’information sur l’opération est égal à 1)

  La simulation `UWOP_PUSH_MACHFRAME` décrémente d’opération RSP de 40 (information sur l’opération est égal à 0) ou 48 (information sur l’opération est égal à 1).

#### <a name="operation-info"></a>Informations sur l’opération

La signification des bits info opération varie selon le code d’opération. Pour encoder un Registre à usage général (entier), ce mappage est utilisé :

|||
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

### <a name="chained-unwind-info-structures"></a>Chaînées structures d’informations de déroulement

Si l’indicateur UNW_FLAG_CHAININFO est défini, puis une structure d’informations de déroulement est secondaire, et le champ adresse exception-Gestionnaire/informations chaînées partagée contient les informations de déroulement principales. Cet exemple de code récupère le réplica principal informations de déroulement, en supposant que `unwindInfo` est la structure qui a le UNW_FLAG_CHAININFO l’indicateur est défini.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Informations chaînées sont utile dans deux situations. Tout d’abord, il peut être utilisé pour les segments de code non contigus. À l’aide des informations chaînées, vous pouvez réduire la taille des informations de déroulement requises, car vous n’êtes pas obligé de dupliquer le tableau de codes de déroulement à partir des informations de déroulement principales.

Vous pouvez également utiliser des informations chaînées pour regrouper les registres volatils. Le compilateur peut différer de l’enregistrement des registres volatils jusqu'à ce qu’il se trouve en dehors du prologue d’entrée de fonction. Vous pouvez l’enregistrer en ayant les informations de déroulement principales pour la partie de la fonction avant le code groupé et configuration des informations chaînées avec une taille différente de zéro du prologue, où les codes de déroulement dans les informations chaînées reflètent les enregistrements des registres non volatils. Dans ce cas, les codes de déroulement sont toutes les instances de UWOP_SAVE_NONVOL. Un regroupement qui enregistre les registres non volatils à l’aide d’un PUSH ou modifie le registre RSP à l’aide d’une allocation de pile fixe supplémentaire n’est pas pris en charge.

Élément UNWIND_INFO dont UNW_FLAG_CHAININFO définie peut contenir une entrée RUNTIME_FUNCTION dont l’élément UNWIND_INFO possède également un UNW_FLAG_CHAININFO défini, parfois appelé *rétraction plusieurs*. Au final, les informations de déroulement chaînées pointeurs arrivent à un élément UNWIND_INFO avec UNW_FLAG_CHAININFO désactivée ; Il s’agit de l’élément UNWIND_INFO principal pointant vers le point d’entrée de procédure réel.

## <a name="unwind-procedure"></a>Procédure de déroulement

Le tableau des codes de déroulement est trié dans l’ordre décroissant. Lorsqu’une exception se produit, le contexte complet est stocké par le système d’exploitation dans un enregistrement de contexte. La logique de répartition d’exception est appelée, qui exécute plusieurs fois ces étapes pour rechercher un gestionnaire d’exceptions :

1. Utilisez le RIP actuel stocké dans l’enregistrement de contexte pour rechercher une entrée de table RUNTIME_FUNCTION qui décrit la fonction active (ou une partie de la fonction, pour les entrées UNWIND_INFO chaînées).

1. Si aucune entrée de table de fonction est trouvée, puis il se trouve dans une fonction de feuille, et RSP répond directement le pointeur de retour. Le pointeur de retour à [RSP] est stocké dans le contexte mis à jour, le RSP simulé est incrémenté de 8 et l’étape 1 est répétée.

1. Si une entrée de table de fonction est trouvée, RIP peut se trouver dans trois régions : a) dans un épilogue, b) dans le prologue ou c) dans le code qui peut être couvert par un gestionnaire d’exceptions.

   - Cas un) si le protocole RIP est dans un épilogue, puis contrôle quitte la fonction, il ne peut y avoir aucun gestionnaire d’exceptions associé à cette exception pour cette fonction et les effets de l’épilogue doivent continuer à utiliser le contexte de la fonction d’appelant de calcul. Pour déterminer si le protocole RIP est dans un épilogue, le flux de code à partir de RIP sur est examiné. Ce flux de code peut être mis en correspondance avec la partie finale d’un épilogue, il se trouve dans un épilogue, puis sur la partie restante de l’épilogue est simulée, avec l’enregistrement de contexte mis à jour en tant que chaque instruction est traitée. Après cela, l’étape 1 est répétée.

   - Cas b) si le protocole RIP se trouve dans le prologue, contrôle n’a pas accédé à la fonction, il ne peut y avoir aucun gestionnaire d’exceptions associé à cette exception pour cette fonction et les effets du prologue doivent être annulés pour calculer le contexte de la fonction d’appelant. Le protocole RIP se trouve dans le prologue si la distance entre le début de la fonction et le protocole RIP est inférieure ou égale à la taille du prologue encodée dans les informations de déroulement. Les effets du prologue sont déroulés en recherchant, dans le tableau de codes de déroulement pour la première entrée avec un décalage inférieur ou égal à l’offset du RIP à partir du début de la fonction, puis en annulant l’effet de tous les éléments restants dans le tableau des codes de déroulement. Étape 1 est ensuite répétée.

   - Cas c) si le protocole RIP n’est pas dans un prologue ou épilogue et la fonction a un gestionnaire d’exceptions (UNW_FLAG_EHANDLER est défini), alors le gestionnaire spécifique au langage est appelé. Le Gestionnaire d’analyse ses données et appelle des fonctions comme il convient de filtre. Le gestionnaire spécifique au langage peut retourner que l’exception a été gérée ou que la recherche doit être poursuivie. Elle peut également initier un déroulement directement.

1. Si le gestionnaire spécifique au langage retourne un état géré, l’exécution se poursuite à l’aide de l’enregistrement de contexte d’origine.

1. Si aucun gestionnaire spécifique à la langue ou le gestionnaire renvoie l’état « continuer la recherche », l’enregistrement de contexte doit être déroulé à l’état de l’appelant. Pour cela, vous devez traiter tous les éléments du tableau du code de déroulement, annulant l’effet de chacune. Étape 1 est ensuite répétée.

Lorsqu’il est chaîné déroulement info est impliqué, ces étapes de base sont toujours suivies. La seule différence est que, tandis que de parcourir le tableau des codes de déroulement pour dérouler les effets d’un prologue, une fois que la fin du tableau est atteinte, il est ensuite lié les informations de déroulement parent et le tableau de code de déroulement ensemble qu’il contient est parcouru. Cette liaison continue jusqu'à arrivant aux informations de déroulement sans l’indicateur UNW_CHAINED_INFO, et il finit ensuite parcourir son tableau des codes de déroulement.

Données de déroulement le plus petit ensemble de 8 octets. Cela représente une fonction qui a affecté uniquement 128 octets de pile ou moins et éventuellement enregistré un Registre non volatil. Il s’agit également la taille de chaînées structure d’informations pour un prologue de longueur nulle avec sans code de déroulement de déroulement.

## <a name="language-specific-handler"></a>Gestionnaire spécifique au langage

L’adresse relative du gestionnaire spécifique au langage est présente dans UNWIND_INFO chaque fois que les indicateurs UNW_FLAG_EHANDLER ou UNW_FLAG_UHANDLER sont définis. Comme décrit dans la section précédente, le gestionnaire spécifique au langage est appelé dans le cadre de la recherche d’un gestionnaire d’exceptions ou dans le cadre d’un déroulement. Il possède ce prototype :

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** fournit un pointeur vers un enregistrement d’exception possédant la définition Win64 standard.

**EstablisherFrame** est l’adresse de la base de l’allocation de pile fixe pour cette fonction.

**ContextRecord** pointe vers le contexte d’exception au moment de l’exception a été levée (dans le cas de gestionnaire d’exceptions) ou en cours « contexte de déroulement » (dans le cas de gestionnaire de terminaisons).

**DispatcherContext** pointe vers le contexte de répartiteur de cette fonction. Il a cette définition :

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

**ControlPc** est la valeur de RIP dans cette fonction. Cette valeur est une adresse de l’exception ou l’adresse à laquelle le contrôle gauche la fonction de l’établissement d’une. Le protocole RIP est utilisé pour déterminer si contrôle est dans une construction protégée à l’intérieur de cette fonction, par exemple, un `__try` bloquer pour `__try` / `__except` ou `__try` / `__finally`.

**ImageBase** est l’image de base (adresse de chargement) du module contenant cette fonction, à ajouter aux offsets de 32 bits utilisés dans l’entrée de fonction et informations de déroulement pour enregistrer des adresses relatives.

**FunctionEntry** fournit un pointeur vers le RUNTIME_FUNCTION fonction d’entrée de la fonction info base d’image adresses relatives et déroulement de cette fonction.

**EstablisherFrame** est l’adresse de la base de l’allocation de pile fixe pour cette fonction.

**TargetIp** fournit une adresse d’instruction facultatif qui spécifie l’adresse de continuation du déroulement. Cette adresse est ignorée si **EstablisherFrame** n’est pas spécifié.

**ContextRecord** pointe vers le contexte de l’exception, pour une utilisation par le code de répartition/déroulement d’exception système.

**LanguageHandler** pointe vers la routine du gestionnaire spécifique au langage appelé.

**HandlerData** pointe vers les données du gestionnaire spécifique au langage pour cette fonction.

## <a name="unwind-helpers-for-masm"></a>Déroulement de l’assistance pour MASM

Pour pouvoir écrire des routines d’assembly approprié, il existe un ensemble de pseudo-opérations qui peut être utilisé en parallèle avec les instructions d’assembly proprement dit pour créer l’approprié .pdata et .xdata. Il existe également un ensemble de macros qui fournissent une utilisation simplifiée des pseudo-opérations pour leurs utilisations les plus courantes.

### <a name="raw-pseudo-operations"></a>Pseudo-opérations brutes

|Opération de pseudo|Description|
|-|-|
|FRAME de PROC \[:*ehandler*]|Causes MASM pour générer une fonction table d’entrée dans .pdata et .xdata d’informations de déroulement pour une fonction de structuré comportement de déroulement de la gestion des exceptions.  Si *ehandler* est présent, cette procédure est entrée dans l’enregistrement .xdata comme gestionnaire spécifique au langage.<br /><br /> Lorsque l’attribut FRAME est utilisé, il doit être suivi par un. Directive ENDPROLOG.  Si la fonction est une fonction de feuille (tel que défini dans [types de fonction](../build/stack-usage.md#function-types)) l’attribut FRAME n’est pas nécessaire, tout comme le reste de ces pseudo-opérations.|
|. PUSHREG *inscrire*|Génère une entrée de code de déroulement UWOP_PUSH_NONVOL pour le numéro de Registre spécifié à l’aide de l’offset actuel dans le prologue.<br /><br /> Cela doit uniquement être utilisé avec les registres d’entiers non volatile.  Pour obtenir des notifications Push registres volatils, utilisez un. 8 ALLOCSTACK, à la place|
|. SETFRAME *inscrire*, *offset*|Renseigne le frame inscrire champ et le décalage dans les informations de déroulement en utilisant le Registre spécifié et le décalage. Le décalage doit être un multiple de 16 et inférieur ou égal à 240. Cette directive génère également une entrée de code de déroulement UWOP_SET_FPREG pour le Registre spécifié à l’aide de l’offset de prologue actuel.|
|. ALLOCSTACK *taille*|Génère un UWOP_ALLOC_SMALL ou UWOP_ALLOC_LARGE avec la taille spécifiée pour l’offset actuel dans le prologue.<br /><br /> Le *taille* opérande doit être un multiple de 8.|
|. SAVEREG *inscrire*, *offset*|Génère un UWOP_SAVE_NONVOL ou une entrée de code de déroulement UWOP_SAVE_NONVOL_FAR pour le Registre spécifié et l’offset à l’aide de l’offset de prologue actuel. MASM choisit l’encodage plus efficace.<br /><br /> *décalage* doit être positif et un multiple de 8. *décalage* est relative à la base du frame de la procédure, qui est généralement dans RSP, ou, si vous utilisez un pointeur de frame, le pointeur de frame non ajustée.|
|. SAVEXMM128 *inscrire*, *offset*|Génère un UWOP_SAVE_XMM128 ou une entrée de code de déroulement UWOP_SAVE_XMM128_FAR pour le registre XMM spécifié et l’offset à l’aide de l’offset de prologue actuel. MASM choisit l’encodage plus efficace.<br /><br /> *décalage* doit être positif et un multiple de 16.  *décalage* est relative à la base du frame de la procédure, qui est généralement dans RSP, ou, si vous utilisez un pointeur de frame, le pointeur de frame non ajustée.|
|. PUSHFRAME \[ *code*]|Génère une entrée de code de déroulement UWOP_PUSH_MACHFRAME. Si le paramètre facultatif *code* est spécifié, l’écriture de code de déroulement reçoit un modificateur de 1. Sinon, le modificateur est 0.|
|.ENDPROLOG|Signale la fin des déclarations de prologue.  Doit se produire dans les 255 premiers octets de la fonction.|

Voici un exemple de prologue de fonction avec une utilisation correcte de la plupart des codes d’opération :

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
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>Macros MASM

Afin de simplifier l’utilisation de la [pseudo-opérations brutes](#raw-pseudo-operations), il existe un ensemble de macros, défini dans ksamd64.inc, qui peut être utilisé pour créer des prologues et épilogues.

|Macro|Description|
|-|-|
|alloc_stack(n)|Alloue un frame de pile de n octets (à l’aide de `sub rsp, n`) et qui émet des informations (.allocstack n) de déroulement appropriées|
|save_reg *reg*, *loc*|Enregistre un Registre non volatil *reg* sur la pile RSP décalage *loc*et qui émet des informations de déroulement appropriées. (.savereg reg, loc)|
|push_reg *reg*|Exécute un push d’un Registre non volatil *reg* sur la pile et émet des informations de déroulement appropriées. (.pushreg reg)|
|rex_push_reg *reg*|Enregistrer un Registre non volatil sur la pile à l’aide d’un push de 2 octets et émet des informations (.pushreg reg) doit être utilisée que si la notification push est la première instruction dans la fonction pour vous assurer que la fonction est corrigeable en chaud-mémoire de déroulement appropriées.|
|save_xmm128 *reg*, *loc*|Enregistre un registre XMM non volatil *reg* sur la pile RSP décalage *loc*et qui émet des informations (.savexmm128 reg, loc) de déroulement appropriées|
|set_frame *reg*, *offset*|Définit le Registre de frame *reg* pour le RSP + *décalage* (à l’aide d’un `mov`, ou un `lea`) et émet des informations (.set_frame reg, offset) de déroulement appropriées|
|push_eflags|Pousse les eflags avec un `pushfq` obtenir des instructions et émet des informations (.alloc_stack 8) de déroulement appropriées|

Voici un exemple de prologue de fonction avec une utilisation correcte des macros :

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Déroulement des définitions de données en C

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

[x64 conventions des logiciels](../build/x64-software-conventions.md)