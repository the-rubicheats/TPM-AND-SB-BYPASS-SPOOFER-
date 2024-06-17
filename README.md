# SOMENTE FUNCIONA PARA WINDOWS 10 22H2
## STATUS - Desconhecido

ANTES DE INICIAR O TUTORIAL TENTE BAIXAR [ISTO](./bypass.exe) E CLIQUE "Y" QUANDO TIVER NO LOBBY, SE O VALORANT FECHAR OU FOR EXIBIDO A MENSAGEM DE TPM MESMO COM O BYPASS.exe ABERTO PROSSIGA COM O TUTORIAL:

### REQUISITOS

#### PASSO 1:
Converta o disco onde você instalará o Windows para uma partição MBR. SIGA ISTO SE VOCÊ NÃO SOUBER COMO:
[https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-gpt-disk-into-an-mbr-disk](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-gpt-disk-into-an-mbr-disk)

#### PASSO 2:
Baixe o arquivo ISO do Ghost Spectre Windows 10 22H2, você pode usar qualquer outro, mas certifique-se de que é 22H2.

#### PASSO 3:
Instale o RUFUS, selecione o USB que você usará para instalar o Windows. CERTIFIQUE-SE DE SELECIONAR MBR NO ESTILO DE PARTIÇÃO.

#### PASSO 4:
Entre no seu BIOS e mude o modo de inicialização para legacy (Pode ser um pouco diferente para diferentes placas-mãe), depois desligue TPM e SB. Após isso, inicie a partir do seu USB.

**INFORMAÇÃO IMPORTANTE:**
Durante a seleção de inicialização, não selecione o drive que está rotulado com UEFI!!! (você não pode instalar o Windows em um disco MBR se estiver em um ambiente EFI). Selecione aquele que está rotulado como USB.

#### PASSO 5:
Exclua todas as partições, exceto aquela que você converteu para MBR, então instale o Windows nela.

#### PASSO 6:
Quando o Windows estiver completamente instalado, pesquise por Informações do Sistema. Verifique se o seu "MODO DE BIOS" está configurado para LEGACY. Se não estiver, comece novamente do PASSO 1.

#### PASSO 7:
Faça spoof do seu PC

##### PASSO 7.01:
FLASH SUA BIOS PARA UMA VERSÃO DIFERENTE. (GOOGLE -- "NOME DA SUA PLACA-MÃE" download da BIOS). Após o flash, CERTIFIQUE-SE DE VERIFICAR SE TPM E SB ESTÃO DESLIGADOS.

##### PASSO 7.1 [para aqueles que não sabem como fazer spoof]:
(RECOMENDO FAZER O PASSO 7.2 em vez disso)

Baixe [ISTO](./spoof.exe)
1. Clique em refresh, tire uma captura de tela do HWID.
2. Clique em spoof. Então seu PC irá reiniciar.
3. Abra novamente, clique em refresh, verifique se tudo mudou.
4. Se não, siga o PASSO 7.2 (Você ainda pode seguir, mesmo que o PASSO 7.1 tenha funcionado, para boas medidas).

##### PASSO 7.2 [para aqueles que não sabem como fazer spoof MÉTODO EFI]:

1-Crie um arquivo .bat e coloque este código dentro dele e execute.

```batch
    ECHO OFF
    TITLE UC CHECKER
    ECHO **********************************
    Color 0F
    ECHO **********************************
    :start
    cls
    wmic diskdrive get model, serialnumber
    ECHO CPU 
    wmic cpu get serialnumber
    ECHO BIOS
    wmic bios get serialnumber
    ECHO Motherboard
    wmic baseboard get serialnumber
    ECHO smBIOS UUID
    wmic path win32_computersystemproduct get uuid
    getmac
    echo Press any key to get your hardware serials again.
    pause>nul
    goto start
```

2-Tire uma captura de tela.
3-Baixe o RUFUS.
4-Selecione seu drive USB, selecione não inicializável e mude o estilo de partição para GPT. Clique em iniciar.
3-Baixe ISTO.

4-Abra o arquivo startup.nsh, e mude todos os HWID's para algo aleatório como isto (LEMBRE-SE, HÁ 2 ARQUIVOS startup.nsh)
```batch
    AMIDEEFIx64.efi /BS VCXZBHJSDGFYUASVDF          <--- ANYTHING RANDOM(any length), DO THIS FOR ALL THE COMMANDS
    except   AMIDEEFIx64.efi /SU AUTO
```

5-Agora, cole-os no seu drive USB. Deve parecer algo assim.
```batch
    USB:
           efi
           afuefix64.efi
           amideefix64.efi
           Startup.nsh
```

6-Agora, reinicie e entre no seu BIOS.
7-Vá para a ORDEM DE BOOT.
8-Atribua a PRIORIDADE DE BOOT #1 (ou algo parecido) ao seu USB.
9-Então, inicie a partir do seu USB.
10-Isso começará a spoofar seu PC (<5 segundos) e seu Windows abrirá automaticamente.
11-Compare o SerialNumber da sua PLACA-MÃE e UUID.
12-Se mudou, você fez spoof com sucesso no seu PC.
13-Se não, abra o arquivo startup.nsh dentro da pasta EFI.
14-Substitua todo o código por isto.
```batch
    fs0:
    startup.nsh
```
15-Ainda não? Mude todos os amideefix64.efi para afuefix64.efi e tente novamente. Assim.
```batch
    AMIDEEFIx64.efi /BS VCXZBHJSDGFYUASVDF    
    to
    afuefix64.efi /BS VCXZBHJSDGFYUASVDF    (do this for both startup.nsh files)
```

#### STEP 8:
Execute o cmd como administrador, cole
```batch
    bcdedit /set hypervisorlaunchtype off
```

#### VOCÊ PODE CONTINUAR USANDO SUA CONTA ANTIGA (em alguns casos, contas antigas receberão um prompt de TPM:
Baixe VALORANT e divirta-se
