# SPDX-License-Identifier: GPL-2.0-only

ccflags-y += -Wmissing-prototypes

# Enabled only when the builder selects the Xiaomi hwid provider.
ifneq ($(strip $(XIAOMI_HWID_ROOT)),)
ccflags-y += -DCNSS_XIAOMI_L3_HWID -I$(XIAOMI_HWID_ROOT)
endif

ifeq ($(CONFIG_CNSS_OUT_OF_TREE),y)
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/cnss_utils
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/inc
else
ccflags-y += -I$(srctree)/drivers/net/wireless/cnss_utils
endif

ifeq ($(CONFIG_CNSS_HW_SECURE_DISABLE), y)
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/../../securemsm-kernel/smcinvoke/
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/../../securemsm-kernel/linux/
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/../../securemsm-kernel/include/linux/
ccflags-y += -I$(WLAN_PLATFORM_ROOT)/../../securemsm-kernel/include/uapi/linux/
endif

obj-$(CONFIG_CNSS2) += cnss2.o

cnss2-y := main.o
cnss2-y += bus.o
cnss2-y += debug.o
cnss2-y += pci.o
cnss2-y += power.o
cnss2-y += genl.o
cnss2-$(CONFIG_PCI_MSM) += pci_qcom.o
cnss2-$(CONFIG_PCIE_QCOM_ECAM) += pci_qcom_ecam.o
cnss2-$(CONFIG_CNSS2_QMI) += qmi.o coexistence_service_v01.o
