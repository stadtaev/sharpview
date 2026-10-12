# Research increment validation

The initial increment uses the existing production projects and a shared xUnit test project. Validation combines extracted fixture facts, independently assembled Core snapshots, in-memory semantic compilations, and fresh CLI processes.

| Requirement | Evidence |
|---|---|
| Controller → application → infrastructure source bindings | `Source_bindings_link_projects_and_preserve_locations`, `Fresh_process_prints_cross_project_chain_and_evidence` |
| Matching, unrelated and incompatible catches; rethrow/replacement | `Exception_witness_uses_protected_call_site` parameter cases |
| Subsequent rethrow/replacement interception and uncertainty | `Changed_exception_retains_subsequent_interception`, `Changed_exception_retains_subsequent_filter_uncertainty` |
| Throws, throw expressions, rethrows, filters and region evidence | `Throw_expression_rethrow_and_filter_facts_are_retained`, `Protected_regions_filters_and_throw_runtime_precision_are_preserved` |
| Static vs exact constructed type, including explicit casts | `Cast_throw_retains_static_type_and_exact_construction_separately`, `Exact_construction_beneath_base_conversion_matches_derived_handler_and_preserves_static_type` |
| Assembly-aware and uncertain type matching | `Same_display_name_in_different_assemblies_does_not_match_handler`, `Different_constructed_generic_arguments_are_not_false_matching_handlers`, `Unbound_exception_type_does_not_skip_typed_handler` |
| Controller conventions and inherited exclusions | `Controller_convention_excludes_abstract_generic_and_inherited_opt_outs` |
| Interface/recursive boundaries and declared/direct policy | `Uncertain_boundaries_are_visible`, `Dispatch_policies_preserve_declared_binding_and_mark_exclusion` |
| Await observation and unsupported async propagation | `Direct_await_observation_and_aliased_task_unknown_are_distinguished`, `Task_exception_requires_direct_observation_before_caller_handler`, `Async_void_and_custom_awaitable_propagation_are_unknown` |
| Action escape with separately reported middleware evidence | `Exceptions_report_action_escape_and_boundary_evidence_separately` |
| Configured layers and call transitions | `Controller_layers_are_explicit_and_distance_is_transitions` |
| Branches, diamonds, cycles and repeated call-site evidence | `Call_paths_do_not_invent_sibling_edges_and_retain_duplicates`, `Diamond_preserves_each_witness_without_global_visited_pruning`, `Cycle_is_path_local_and_does_not_hide_sibling_leaf` |
| Depth/work/output limits and cancellation | `Graph_limits_are_honest_and_cancellation_is_observed`, `Exact_output_and_work_budget_at_natural_end_is_not_truncation`, `Depth_and_work_stops_report_unknown_instead_of_claiming_no_exceptions`, `Traversal_limits_have_nonzero_status_and_visible_marker` |
| Constructors/accessors/operators and nested callable ownership | `Expression_bodied_property_and_base_accessor_have_source_and_direct_dispatch`, `Operators_conversions_and_type_only_declarations_are_not_lost`, `Nested_callables_own_calls_without_invented_parent_edges` |
| Partial/reduced generic binding and dependencies | `Partial_methods_reduced_extensions_and_nested_generic_dependencies_keep_identity` |
| Generated exclusion and evidence | `Generated_exclusion_has_explicit_evidence` |
| SDK .csproj/.sln/.slnx loading and framework selection | `Project_input_includes_source_references_and_cross_project_bindings`, `Conventional_solution_input_preserves_cross_project_source_facts`, `Framework_selection_uses_conditional_assets_and_rejects_ambiguity`, research fixture loading |
| No implicit restore, source preservation and output safeguard | `Missing_restoration_is_rejected_without_creating_assets_or_changing_source`, `Output_refuses_to_overwrite_an_input_file` |
| Argument failures before loading, IDs and deterministic JSON | `Invalid_options_fail_before_loading`, `Snapshot_ids_round_trip_and_json_is_deterministic` |

Reproduce with `dotnet build tests/Fixtures/ResearchSolution/ResearchSolution.slnx`, `dotnet build sharpview.slnx --no-incremental`, and `dotnet test sharpview.slnx`. Reports are in `docs/samples`.

The self-analysis smoke check loaded Sharpview's four projects and exported 834 callable facts, 2,649 call sites, 32 throw sites and four catches with 93 explicitly recorded gaps. This checks loading/extraction on the host's own code; it does not replace an external Web API experiment.
