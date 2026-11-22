# Ansible Node Exporter Role

## اجرا

1. آی‌پی سرورها و متغیرهای هر محیط را در فایل‌های `inventory/prod.ini` یا `inventory/stage.ini` وارد کنید.
2. پیش‌نیازهای کالکشن Ansible (در صورت استفاده از فایروال) را نصب کنید:
   ```bash
   ansible-galaxy collection install ansible.posix community.general
   ```
3. پلی‌بوک را اجرا کنید:
   ```bash
   ansible-playbook -i inventory/prod.ini deploy_node_exporter.yml
   ```
