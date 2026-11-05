# gercom_fedavg-smart-homes

Bancada de **Aprendizado Federado para Redes Neurais (MLP)** utilizando o framework **Flower (`flwr`)** e **PyTorch**, aplicada à previsão de consumo energético predial sobre o dataset UCI *Appliances Energy Prediction*.

Desenvolvido no **Laboratório GERCOM / UFPA** como fundação experimental para as pesquisas em agregação federada de telemetria predial.

---

## 🏛️ Arquitetura do Sistema

1. **Modelo Neural (PyTorch):**
   - Rede neural densa MLP (22 atributos de entrada $\to$ 10 $\to$ 5 $\to$ 3 $\to$ 1 saída de consumo de energia) com ativações ReLU intermediárias.
2. **Dataset de Sensores Ambientais:**
   - Ingestão de séries temporais de smart homes: 9 temperaturas internas ($T_1 \dots T_9$), 9 umidades relativas ($RH_1 \dots RH_9$), temperatura externa ($T_{out}$), pressão e umidade externa.
3. **Federalização com Flower:**
   - Implementação de subclasse customizada de `flwr.client.NumPyClient`.
   - Conversão em tempo real de tensores PyTorch (`state_dict`) para arrays NumPy transmitidos nas rodadas de agregação central (FedAvg).

---

## 📦 Como Executar

```bash
# 1. Clonar repositório
git clone https://github.com/Julio-C-Oliveira/gercom_fedavg-smart-homes.git
cd gercom_fedavg-smart-homes

# 2. Configurar ambiente
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3. Executar simulação federada
cd FedAVG_PyTorch_and_Flower_Linear_Regression
python3 server.py &
python3 client.py
```

---

## 📄 Licença
Distribuído sob a licença MIT. Veja `LICENSE` para mais detalhes.
