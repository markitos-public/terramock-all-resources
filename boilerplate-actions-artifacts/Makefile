.PHONY: image run delete help default publish tf-clean tf-format tf-validate tf-init tf-plan tf-apply tf-destroy

default: help

help:
	chmod +x ./bin/make-help.sh
	./bin/make-help.sh

image:
	@if ! echo "$(version)" | grep -Eq '^(local|google)=[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version="local=n.n.n" o version="google=n.n.n" (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-image.sh
	./bin/make-image.sh $(version)

run:
	@if ! echo "$(version)" | grep -Eq '^(local|google)=[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version="local=n.n.n" o version="google=n.n.n" (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-run.sh
	./bin/make-run.sh $(version)


delete:
	@if ! echo "$(version)" | grep -Eq '^[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version=n.n.n (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-delete.sh
	./bin/make-delete.sh $(version)

tag:
	@if ! echo "$(version)" | grep -Eq '^[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version=n.n.n (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-tag.sh
	./bin/make-tag.sh $(version)

delete-tag:
	@if ! echo "$(version)" | grep -Eq '^[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version=n.n.n (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-delete-tag.sh
	./bin/make-delete-tag.sh $(version)

publish:
	@if ! echo "$(version)" | grep -Eq '^[0-9]+\.[0-9]+\.[0-9]+$$'; then \
	  echo '❌ ERROR: Debes pasar version=n.n.n (semver)'; \
	  exit 2; \
	fi
	chmod +x ./bin/make-publish.sh
	./bin/make-publish.sh $(version) $(project_id)

tf-clean:
	rm -rf .terraform
	rm -f *.tfstate *.tfstate.backup .terraform.lock.hcl

tf-format:
	@echo "Formatting Terraform files..."
	terraform fmt -recursive
	@echo "Terraform files formatted."

tf-validate:
	@echo "Validating Terraform files..."
	terraform validate
	@echo "Terraform files validated."

tf-init:
	@echo "Initializing Terraform..."
	terraform init
	@echo "Terraform initialized."
	
tf-plan:
	@echo "Planning Terraform changes..."
	terraform plan
	@echo "Terraform plan completed."

tf-apply:
	@echo "Applying Terraform changes..."
	terraform apply -auto-approve
	@echo "Terraform changes applied."

tf-destroy:
	@echo "Destroying Terraform resources..."
	terraform destroy -auto-approve
	@echo "Terraform resources destroyed."